---
title: Moving to Azure DevOps
description: "This project tried to move from https://github.com/SummittDweller/eleventy-blog to Azure DevOps and https://summittdweller@dev.azure.com/summittdweller/My-Eleventy-Blog/_git/My-Eleventy-Blog.  It failed."  
tags: post
date: "Created"
layout: layouts/post.njk
last_modified_at: 2023-02-01T21:04:57
---

Not much to tell you here except that the blog was moved from a GitHub workflow and repository, to Azure DevOps so any/all mentions of https://github.com/SummittDweller/eleventy-blog in past posts are ~now equivalent to https://summittdweller@dev.azure.com/summittdweller/My-Eleventy-Blog/_git/My-Eleventy-Blog~ still valid.  

# Pipeline Errors

So, in the Azure Pipelines there's an option to select an "Existing Azure Pipelines YAML file" and I choose that, incorrectly.  When I applied my old `.github/workflows/azure-static-web-apps-white-cliff-08b1f8010.yml` as a pipeline it didn't work, naturally.  Fortunately, I soon found [How to Publish Azure Static Web Apps with Azure DevOps](https://juarezjunior.medium.com/how-to-publish-azure-static-web-apps-with-azure-devops-4d21146e879e) and am working through that "proper" procedure now.  

# Removing the Errant Pipeline

I have yet to find any guidance telling me how to remove that errant `.github/workflows/azure-static-web-apps-white-cliff-08b1f8010.yml` pipeline, so I'm just going to remove that file (moving it to an `.out-of-the-way` directory) and see what happens.  


Now you know.  That's all, FOR NOW, folks!    