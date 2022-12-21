---
title: Deploying to Azure
description: Another post that's not specific to Eleventy, but important nonetheless. 
tags: post
date: "Created"    # date: "git Last Modified"
layout: layouts/post.njk
last_modified_at: 2022-12-21T21:45:38
---

Ok, this post never was specific to `Eleventy`, but I wanted to capture it anyway.  On the posted date I followed the guidance from [Deploying an 11ty Site to Azure Static Web Apps](https://squalr.us/2021/05/deploying-an-11ty-site-to-azure-static-web-apps/) to host this blog on _Azure_.

After fumbling through the far-too-thick _Azure_ subscription and app configuration process (took more than an hour...there were complications, naturally) I now have:

  - https://white-cliff-08b1f8010.2.azurestaticapps.net  

Moments ago I updated my _Azure_ `Dashboard` | `My-Eleventy-Blog` | `Configuration` | `Application settings` to include a parameter with Name = `TZ` and Value = `America/Chicago`.  Hopefully that will correct the look of my date/times.   
