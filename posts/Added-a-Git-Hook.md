---
title: Added a Git Hook 
description: Not specific to Eleventy, but important nonetheless. 
tags: post
date: "Created"
# date: "git Last Modified"
layout: layouts/post.njk
last_modified_at: 2022-12-21T20:28:52
---

Ok, this post wasn't originally specific to `Eleventy`, but I think it's important and worth noting here.  On the posted date I followed my own advice from [Creating a Git Hook](https://static.grinnell.edu/dlad-blog/posts/131-creating-a-git-hook/) and applied it to this blog.  But then I found a better `Eleventy` way in https://www.11ty.dev/docs/dates/.     

So, I changed the front matter of this post to read `date: "git Last Modified"`, but that broke the site with an error like `[11ty] mapA.date.getTime is not a function (via TypeError)`.  So, I changed the front matter to include both `date: "Created"` and `last_modified_at:`.  That works, and now I'm playing with a new `readableDT` filter I created in `.eleventy.js` and added to render `last_modified_at` as a date/time in `post.njk`.     
