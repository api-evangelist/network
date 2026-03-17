---
name: gather-properties
description: Scans all apis.yml files in /Users/kinlane/GitHub/all and compiles a unique list of all properties used at the top level, api level, common level, and inside property/contact entries, then writes the result to /Users/kinlane/GitHub/all/network/properties.yml.
allowed-tools: Bash, Write, Read
---

# Gather Network Properties

Scan all `apis.yml` files across every repo in `/Users/kinlane/GitHub/all`, collect every unique property key used at every structural level, and write the result to `/Users/kinlane/GitHub/all/network/properties.yml`.

## Steps

1. Iterate over every subdirectory in `/Users/kinlane/GitHub/all` (skip hidden dirs and node_modules).
2. For each repo, parse `apis.yml` and extract unique property keys from:
   - Top-level keys (root of the document)
   - Keys inside each entry under `apis:`
   - Keys inside each entry under `common:` or `commonProperties:`
   - Keys inside each entry under `properties:` within api entries
   - Keys inside each entry under `contact:` or `maintainers:`
   - Values of `type` fields (for property type inventory)
3. Deduplicate all keys across all files per level.
4. Write `/Users/kinlane/GitHub/all/network/properties.yml` with today's date and all properties organized by level.
5. Commit the updated file in the `network` repo.

## Implementation

Run this Python script via Bash:

```python
import os, yaml
from collections import defaultdict, Counter
from datetime import date

base = "/Users/kinlane/GitHub/all"

top_level_keys = Counter()
api_level_keys = Counter()
common_level_keys = Counter()
property_level_keys = Counter()
contact_level_keys = Counter()
property_types = Counter()

def extract_keys(obj, counter):
    if isinstance(obj, dict):
        for k in obj:
            counter[k] += 1

for repo in sorted(os.listdir(base)):
    if repo.startswith('.'):
        continue
    apis_yml = os.path.join(base, repo, 'apis.yml')
    if not os.path.exists(apis_yml):
        continue
    try:
        with open(apis_yml, 'r', errors='ignore') as f:
            data = yaml.safe_load(f.read())
        if not isinstance(data, dict):
            continue

        extract_keys(data, top_level_keys)

        for api in (data.get('apis') or []):
            if isinstance(api, dict):
                extract_keys(api, api_level_keys)
                for prop in (api.get('properties') or []):
                    if isinstance(prop, dict):
                        extract_keys(prop, property_level_keys)
                        if 'type' in prop:
                            property_types[str(prop['type'])] += 1
                for contact in (api.get('contact') or []):
                    if isinstance(contact, dict):
                        extract_keys(contact, contact_level_keys)

        for common in (data.get('common') or data.get('commonProperties') or []):
            if isinstance(common, dict):
                extract_keys(common, common_level_keys)
                if 'type' in common:
                    property_types[str(common['type'])] += 1

        for prop in (data.get('properties') or []):
            if isinstance(prop, dict):
                extract_keys(prop, property_level_keys)
                if 'type' in prop:
                    property_types[str(prop['type'])] += 1

        for m in (data.get('maintainers') or []):
            if isinstance(m, dict):
                extract_keys(m, contact_level_keys)

    except Exception:
        pass

today = date.today().strftime('%Y-%m-%d')

def render_keys(counter):
    lines = []
    for k in sorted(counter.keys()):
        lines.append(f"    - name: {k}")
        lines.append(f"      count: {counter[k]}")
    return "\n".join(lines)

output = f"""name: API Evangelist Network Properties
description: All properties employed across apis.yml files in the API Evangelist network, organized by level.
url: https://raw.githubusercontent.com/api-evangelist/network/refs/heads/main/properties.yml
created: '2026-03-16'
modified: '{today}'

topLevel:
  description: Properties used at the root level of an apis.yml file.
  properties:
{render_keys(top_level_keys)}

apiLevel:
  description: Properties used inside individual entries under the apis array.
  properties:
{render_keys(api_level_keys)}

commonLevel:
  description: Properties used inside entries under the common or commonProperties array.
  properties:
{render_keys(common_level_keys)}

propertyLevel:
  description: Properties used inside entries under the properties array.
  properties:
{render_keys(property_level_keys)}

contactLevel:
  description: Properties used inside contact and maintainer entries.
  properties:
{render_keys(contact_level_keys)}

propertyTypes:
  description: Known values for the type field used in properties and common entries, with occurrence counts.
  types:
{render_keys(property_types)}
"""

with open(f"{base}/network/properties.yml", "w") as f:
    f.write(output)

print(f"Written properties.yml")
print(f"  Top-level keys: {len(top_level_keys)}")
print(f"  API-level keys: {len(api_level_keys)}")
print(f"  Common-level keys: {len(common_level_keys)}")
print(f"  Property-level keys: {len(property_level_keys)}")
print(f"  Contact-level keys: {len(contact_level_keys)}")
print(f"  Property types: {len(property_types)}")
```

Then commit:

```bash
cd /Users/kinlane/GitHub/all/network
git add properties.yml
git commit -m "Update properties.yml with complete network property inventory

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>"
```

## Output Format

```yaml
name: API Evangelist Network Properties
description: All properties employed across apis.yml files in the API Evangelist network, organized by level.
url: https://raw.githubusercontent.com/api-evangelist/network/refs/heads/main/properties.yml
created: '2026-03-16'
modified: '2026-03-16'

topLevel:
  description: Properties used at the root level of an apis.yml file.
  properties:
    - name: aid
      count: 412
    - name: apis
      count: 890
    ...

apiLevel:
  ...

commonLevel:
  ...

propertyTypes:
  ...
```

## Notes

- Keys are case-sensitive.
- `common` and `commonProperties` are treated as the same level.
- The `created` date is fixed; only `modified` updates on each run.
- After writing, commit the file in the `network` repo.
