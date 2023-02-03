---
title: Moving to Azure DevOps
description: "This project tried to move from https://github.com/SummittDweller/eleventy-blog to Azure DevOps and https://summittdweller@dev.azure.com/summittdweller/My-Eleventy-Blog/_git/My-Eleventy-Blog.  It failed."  
tags: post
date: "Created"
layout: layouts/post.njk
last_modified_at: 2023-02-03T11:48:39
---

Not much to tell you here except that the blog was moved from a GitHub workflow and repository, to Azure DevOps, then back to GitHub, so any/all mentions of https://github.com/SummittDweller/eleventy-blog in past posts are ~now equivalent to https://summittdweller@dev.azure.com/summittdweller/My-Eleventy-Blog/_git/My-Eleventy-Blog~ still valid.  

# Azure Pipelines

Azure DevOps replaces GitHub Actions in Azure with "Azure Pipelines".  I'm not a fan.  Microsoft had such a good thing going in GitHub Actions that I just assumed Pipelines would leverage that.  Nope, and that's largely why I moved back to GitHub with this.  

# Pipeline Errors

So, in the Azure Pipelines there's an option to select an "Existing Azure Pipelines YAML file" and I choose that, incorrectly.  When I applied my old `.github/workflows/azure-static-web-apps-white-cliff-08b1f8010.yml` as a pipeline it didn't work, naturally.  Fortunately, I soon found [How to Publish Azure Static Web Apps with Azure DevOps](https://juarezjunior.medium.com/how-to-publish-azure-static-web-apps-with-azure-devops-4d21146e879e) and am working through that "proper" procedure now.  

# Removing the Errant Pipeline

I have yet to find any guidance telling me how to remove that errant `.github/workflows/azure-static-web-apps-white-cliff-08b1f8010.yml` pipeline, so I'm just going to remove that file (moving it to an `.out-of-the-way` directory) and see what happens.  

Ok, I managed to get a "correct" Pipeline into place after removing the errant one.  Unfortunateluy, that's when I discovered that to run a Pipeline in the free tier of Azure DevOps you have to be "granted permission" and that's a two to three-day process with no guarantee of success.  :frowning:  You can, of course, pay for the right to run a Pipeline, but I'm not inclined to do that either when GitHub Actions are free AND very capable.  

# Moving Back to GitHub

So, this experimental blog has officially moved back to GitHub, specifically to [https://github.com/SummittDweller/my-eleventy-blog](https://github.com/SummittDweller/my-eleventy-blog) with CI/CD deployment via GitHub Actions to [My Eleventy Blog](https://eleventy.summittservices.com/).  

# A New/Old Path Forward

My goal now with this blog is to introduce [NetlifyCMS](https://www.netlifycms.org/) into a site that's NOT hosted in [Netlify.com](https://www.netlify.com/).  I'd also like to see if I can make [StatiCrypt](https://www.npmjs.com/package/staticrypt) work for selected pages.  My target for all of the above is [my Azure Services portal](https://portal.azure.com/#home) leveraging [GitHub Actions](https://github.com/features/actions) for CI/CD deployment and all of the associated heavy-lifting.  

## The NetlifyCMS Piece

I found what looks like a wonderful guide at [jahlen/hugo-azure-static-webapp](https://github.com/jahlen/hugo-azure-static-webapp).    

## The StatiCrypt Piece

In addtion to the implementation shown above, I'd like to also engage [StatiCrypt](), as previously mentioned, and I found a "guide" without much guidance or documentation :frowning:  Fortunately, this "guide" at [Jack-alope/staticrypt-github-actions](https://github.com/Jack-alope/staticrypt-github-actions) does include a key example [`encrypt.yml` file](https://github.com/Jack-alope/staticrypt-github-actions/blob/main/.github/workflows/encrypt.yml).  

## An Eleventy Spin

I'm also interested in doing all of the above with [Eleventy](https://www.11ty.dev/), so I found [Setup Netlify CMS with Eleventy](https://www.seanmcp.com/articles/setup-netlify-cms-with-eleventy/) for guidance.  

# Coordination

All of the pertinent aforementioned resources should be available in a single [OneTab](https://addons.mozilla.org/en-US/firefox/addon/onetab/) that I've saved as a webpage at: https://www.one-tab.com/page/1cYmhYFrSZ2OMY9A0hBMYg.  

---

Let's take these three bits of wisdom for a spin, eh?  
