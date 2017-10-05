---
published: true
layout: post
title: Show The API Call Behind Each Dashboard Visualization
date: 2017-10-05T11:00:00.000Z
tags:
  - API Evangelist
  - Network
  - Visualizations
  - User Interface
  - Politics of APIs
image: 'https://s3.amazonaws.com/kinlane-productions/kentik/kentik_API_menu-300w.png'
---
<p><a href="https://www.kentik.com/kentik-apis-enable-multi-solution-integration/"><img src="https://s3.amazonaws.com/kinlane-productions/kentik/kentik_API_menu-300w.png" width="35%" style="padding: 15px;" /></a></p>I am a big fan of user interfaces that bring APIs out of the shadows. Historically, APIs are often a footnote in the software as a service (SaaS) world, available as a link way down at the bottom of the page, in the settings, or help areas. Rarely, are APIs made a first class citizen in the operations of a web application, which really just perpetuates the myth that APIs aren't for everybody, and the "normals" shouldn't worry their little heads about it. When in reality, EVERYBODY should know about APIs, and have the opportunity to put them to work, so we should stop burying the links to our APIs, and our developer areas. If your API is too technical for a business user to understand what is going on, then you should probably get to work simplifying it, not burying it and keeping it in developer and IT realm.

I have written before about [how DNS provider CloudFlare provides an API behind every feature in their user interface](https://apievangelist.com/2016/10/24/the-api-behind-every-feature-in-the-user-interface/), and I've found [another great example of this over at the network API provider Kentik](https://www.kentik.com/kentik-apis-enable-multi-solution-integration/). In their network dashboard visualization tooling they provide a robust set of tooling for accessing the data behind the visuals, allowing you to export, view SQL, show API call, and enter share view. In their post, they proceed to instruction about how you can get your API key as part of your account, as well as providing a pretty robust introduction into why APIs are important. This is how ALL dashboards should work in my opinion. Any user should be introduced to APIs, and have the ability to get at the data behind, and export it, or directly make an API call in their browser or at the command line.

Developers like to think this stuff should be out of reach of the average user, but that is more about our own insecurities, and power trips, than it is about the average users ability to grasp this stuff. There is no reason why ALL user interfaces can't be developed on top of APIs, with native functionality for getting at the API call, as well as the data, content, or algorithms behind the user interface feature. It makes for more powerful user interfaces, as well as more educated, literate, and efficient power users of our applications. If all web applications operated this way, we'd see a much more API literate business world, where users would be asking more questions, curious about how things work, and experimenting with ways they can be more successful in what they do. While I do see positive examples like Kentik out there, I also find that many web application developers are further retreating from APIs being front and center, preferring to keep them in the shadows of web and mobile applications, out of the reach of the average user. Something we need to reverse.
