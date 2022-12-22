---
title: Added the SummittServices.com Custom Apex Domain 
description: Another seemingly non-Eleventy post, but vitally important nonetheless. 
tags: post
date: "Created"    # date: "git Last Modified"
layout: layouts/post.njk
last_modified_at: 2022-12-22T15:11:10
---

To fully understand this post, please read [Deploying to Azure](/posts/Deploying-to-Azure) first.

After deploying this _Eleventy_ blog to _Azure_ I wanted to give it a suitable and memorable name/address and chose `Eleventy.SummittServices.com`.  To make that possible I had to "move" my `SummittServices.com` apex domain to _Azure_ DNS as well, and validate it there.  So, I found some more far-too-thick _Azure_ DNS guidance (again this took more than an hour...there were complications, naturally) and I now have [this blog](https://eleventy.summittservices.com) hosted as:  

  - https://eleventy.summittservices.com, an alias for  

  - https://white-cliff-08b1f8010.2.azurestaticaps.net  

The effort to get `SummittServices.com` into _Azure_'s DNS and complete the configuration was, as mentioned, not easy.  I dearly wish _Azure_ had up-to-date, human-readable (meaning a human with no MS certifications and less than 1000 hours of MS training) documentation!  

For anyone interested in following along at home, the pertinent documentation all begins with [Custom domains with Azure Static Web Apps](https://learn.microsoft.com/en-us/azure/static-web-apps/custom-domain).  I tried my best to follow the guidance in-sequence, but there were some places where my interface didn't conform to what was written, so I stumbled through it.  Note that I did not configure a landing site for the apex domain, `SummittServices.com`, nor did I create a `www` subdomain, nor any email server configuration.  That will all come later.   
