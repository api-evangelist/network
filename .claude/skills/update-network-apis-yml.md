---
name: update-network-apis-yml
description: Syncs the network apis.yml with all public repositories in the api-evangelist GitHub organization that have an apis.yml file.
user_invocable: true
---

# Update Network apis.yml

Synchronize the network `apis.yml` file with all public repositories in the `api-evangelist` GitHub organization.

## Steps

1. **Fetch all public repos** from the `api-evangelist` GitHub organization:
   ```bash
   gh api orgs/api-evangelist/repos --paginate -q '.[].name' | sort > /tmp/all_repos.txt
   ```

2. **Extract current repo slugs** from the network `apis.yml` by parsing the URLs:
   ```bash
   grep 'url:.*api-evangelist/' apis.yml | sed 's|.*api-evangelist/\([^/]*\)/.*|\1|' | sort -u > /tmp/current_repos.txt
   ```

3. **Find missing repos** (in GitHub but not in apis.yml):
   ```bash
   comm -23 /tmp/all_repos.txt /tmp/current_repos.txt
   ```

4. **Check which missing repos have an `apis.yml` file** by checking for HTTP 200 at:
   `https://raw.githubusercontent.com/api-evangelist/{repo}/refs/heads/main/apis.yml`

   Only repos with a valid `apis.yml` should be added to the network.

5. **Determine display names** for each new repo. Use the GitHub repo description if it provides a clear product/company name. Otherwise, convert the repo slug to title case (e.g., `adobe-experience-cloud` -> `Adobe Experience Cloud`).

6. **Add new entries** to the `network:` section of `apis.yml` in alphabetical order (case-insensitive). Each entry follows this format:
   ```yaml
   - name: Display Name
     url: https://raw.githubusercontent.com/api-evangelist/{repo-slug}/refs/heads/main/apis.yml
   ```

7. **Check for stale entries** — repos listed in `apis.yml` but no longer present in the GitHub organization. Remove any stale entries.

8. **Update the `modified` date** in the header to today's date.

9. **Commit and push** with a descriptive commit message summarizing what was added/removed.

## Important Notes

- The `network` repo itself should NOT be included as a network entry (it is the index file).
- Infrastructure/meta repos (e.g., `config`, `website`, `blueprints`) that don't have an `apis.yml` file should be skipped.
- The `apis.yml` uses the apis.json/yml 0.19 specification format.
- There are 2400+ repos in the organization — use pagination when fetching from the GitHub API.
