---
title: My First Eleventy Experience 
description: "This is the `README.md` file from my first Eleventy experience at https://github.com/SummittDweller/eleventy-blog."
tags: post
date: 2022-12-21T12:38:25-06:00
layout: layouts/post.njk
last_modified_at: 2022-09-26T12:00:29-05:00
---

# eleventy-blog

Built from https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website

## Project Structure

`.`  
`├── .eleventyignore`    <--- See section [.eleventyignore](#eleventyignore) for details.  
`├── about`              <--- A directory for our `About` page.  See [Creating the About Page](#creating-the-about-page).  
`│   └── index.md`       <--- The Markdown content of `About`.  
`├── css`                <--- Holds our site's [CSS stylesheets](#style-and-javascript).   
`│   └── style.css`      <--- Primary CSS stylesheet imported from a CDN. See [Style and Javascript](#style-and-javascript).  
`├── _data`              <--- `_data` is home to [global data files](#global-data).  
`│   └── site.json`      <--- Holds `site.key` global data key:value pairs. See [global data](#global-data).  
`├── _includes`          <--- `_includes` is home to many non-content files.  
`│   ├── layouts`        <--  `layouts` is home to our [layout templates](#layout-templates).  
`│   │   ├── base.njk`   <--- Basic HTML5 boilerplate is the foundation for all the pages.    
`│   │   ├── page.njk`   <--- HTML5 boilerplate adds elements to each page.  See [Creating the About Page](#creating-the-about-page).   
`│   │   └── post.njk`   <--- HTML5 boilerplate adds elements to each `post` page found in `posts`.  
`│   └── nav.njk`        <--- A navigation [partial](#including-partials) to be "included" so don't put it in `layouts`!  
`├── index.njk`          <--- Our home page!  See [Home Page Using Nunjucks](#home-page-using-nunjucks) and later [Collections](#collections).    
`├── node_modules`       <--- See [Initialization](#initialization).  
`├── package.json`       <--- See [Initialization](#initialization).  
`├── package-lock.json`  <--- See [Initialization](#initialization).  
`├── posts`              <--- A custom content type, or "collection".  See [#creating-posts-more-than-just-a-page].  
`│   ├── first-post.md`  <--- An individual collection element page, a `post` in Markdown.  
`│   ├── second-post.md` <--- An individual collection element page, a `post` in Markdown.  
`│   └── third-post.md`  <--- An individual collection element page, a `post` in Markdown.  
`└── _site`              <--- [Build or Start the Site](#build-or-start-the-site). `_site` is our generated static site.  
`    ├── about`  
`    │   └── index.html`  
`    ├── css`  
`    │   └── style.css`  
`    ├── index.html`  
`    └── posts`  
`        ├── first-post`  
`        │   └── index.html`  
`        ├── second-post`  
`        │   └── index.html`  
`        └── third-post`  
`            └── index.html`  


# Initialization

`pacakge.json`, `node_modules` directory, and `package-lock.json`

```
npm init -y
npm install -D @11ty/eleventy
```

The commands above create and populate the `package.json`, `package-lock.json` and `node_modules` files and directory in the project root.  Specifically,  

  - `npm init -y` initializes the node.js project and creates the files and directory, then  
  - `npm install -D @11ty/eleventy` installs _11ty_ in the project.  

# Home Page Using Nunjucks

The `index.njk` file represents the site's home page as a [Nunjucks](https://mozilla.github.io/nunjucks/) template.  The `.njk` extension tells _Eleventy_ to expect _Nunjucks_ syntax.  

# Build or Start the Site

Use `npm run build` (note that the `build` "command" is defined in the `scripts.build` element of `package.json`) to create the site and create/update the contents of the `_site` directory.  

Use `npm run start` (like `build`, the `start` "command" is defined in the `scripts.start` element of `package.json`) to create/update the contents of the `_site` directory AND launch a local webserver hosting the site at [http://localhost:8080](http://localhost:8080).  

# .eleventyignore

The file named `.eleventyignore` specifies a list of files or paths that should be ignored by _Eleventy_ when building the site.  Since this `README.md` file contains snippets of _Nunjucks_ and other template syntax, it is important that `README.md` is included in the `.eleventyignore` file.  Failing to "ignore" documentation files like this one can lead to build failures so don't overlook this feature!    

In this project `.eleventyignore` contains this:  

```
README.md
node_modules/**  
```

# Layout Templates

The `_includes` directory is home to many non-content directories and files.  The `layouts` directory inside `_includes` is key, it holds all of our template files.  Those templates include:

  - `base.njk` - basic HTML5 boilerplate that will serve as the foundation for all the pages on the website.  
  - `page.njk` -   
  - `post.njk` - Introduced later.  This will serve as the foundation for all the _post_ type pages on the website.  

## Understanding Templates

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>{{ title }}</title>
  </head>
  <body>
    <header>{% include "nav.njk" %}</header>
    <main>
    {{ content | safe }}
    </main>
  </body>
</html>
```

In our `layouts` templates, like `base.njk` shown above, text in double curly braces are variables that will be replaced accordingly when a derivative page is being built. The `{{ title }}` variable will be supplied through the page’s front matter block while the `{{ content }}` will be replaced with all incoming page content that is not part of the front matter. The latter is piped through the `safe` filter to prevent it from being escaped.

```html
---
title: Homepage
layout: layouts/base.njk
---

<h1>Welcome to this brand new Eleventy website!</h1>
```

In content files like `index.njk` shown above, the text inside the triple dashes constitute the front matter of the file, while the rest of the file is what will be passed to your layouts as its content. In the front matter, the `title` and `layout` of the file are specified using appropriately named `key:value` pairs.  

# Including Partials

```html
<nav class="navbar is-light" role="navigation" aria-label="main navigation">
  <div class="navbar-start">
    <div class="navbar-item has-text-weight-bold">
      My Eleventy Blog
    </div>
  </div>
  <div class="navbar-end">
    <a href="/" class="navbar-item">
      Home
    </a>

    <a href="/about" class="navbar-item">
      About Me
    </a>
  </div>
</nav>
```

A `partial`, like `nav.njk` shown above, is a template "fragment" that can be **"included" inside the content** portion of another template.  This is different than our previously defined template, `base.njk`, which is **referenced from the front matter** of other templates or content.  The _Nunjucks_ syntax for including a partial looks like this `{% include "nav.njk" %}` example from the `<header>` tag of our `base.njk` file.

# Global Data

```json
{
  "title": "My Eleventy Blog",
  "url": "https://example.com/",
  "language": "en-US",
  "description": "A simple blog with awesome content"
}
```

_Eleventy_ also features [global data files](https://www.11ty.dev/docs/data-global/) like the `site.json` file shown above.  Global data files are JSON files placed in a `_data` directory at the project root that provide global data accessible to all template files.  In global data files, key:value pairs like the ones shown above can be referenced in our templates using syntax like...  

```
      {{ site.title }}  
```

...where the name of the global data file becomes the leading portion of the variable name.  In the example above `{{ site.title }}` will be replaced in the page by the value of the `title` key from the `site.json` file.  

Other data files can be created and used as needed.  For example, you could have an `author.json` file in `_data` that contains your personal details such as your name, bio, and links to your social media profiles. Such data could then be accessed through variables (such as `{{ author.bio }}`) on any page of the website.

# Style and Javascript

When the [How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) tutorial was written, _Eleventy_ did not recognize CSS files for auto-inclusion in the build directory, so a few extra steps were needed to get this working...

  - Create a stylesheet directory, and 
  - Ensure that it is copied over to the build output (`_site`) when the site is built. 
  - Ensure that modifying a stylesheet triggers a rebuild and automatic refreshing in the web browser using a Javascript configuration file for this _Eleventy_ project.

I did these things by...

  - Creating a `css` folder followed by a `style.css` file within it.  `style.css` will import the _Bulma CSS_ framework by using `@import "https://cdn.jsdelivr.net/npm/bulma@0.9.2/css/bulma.min.css";`
  - Creating an `.eleventy.js` file in the project root.  This is the configuration file for _Eleventy_, similar to `_config.yml` files in _Jekyll_ projects.  Note that this file, prefixed with a `.` will be hidden in your filesystem.
  - Update `base.njk` to link in the `/css/style.css` on every page like so:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="/css/style.css" />
    <title>{{ title }}</title>
  </head>
  <body>
    <header>{% include "nav.njk" %}</header>
    <main>
      {{ content | safe }}
    </main>
  </body>
</html>
```  
  
The contents of `.eleventy.js` is:

```js
module.exports = function (eleventyConfig) {
  // Copy the `css` directory to the output
  eleventyConfig.addPassthroughCopy('css');

  // Watch the `css` directory for changes
  eleventyConfig.addWatchTarget('css');
};
```

The above changes cannot be automatically picked up if your local site is running using `npm run start`, so you need to stop the server with `Ctrl+C`, and start it again with `npm run start` before the changes take effect. You’ll need to do this every time you modify the configuration file.

### CSS Using a Plug-In

I used the CSS and Javascript introduction above because it just works, and I believe it helps to understand "how" things work, but frankly there's a better way.  I highly recommend using an _Eleventy_ [plug-in](https://www.11ty.dev/docs/plugins/) for things like style.  The [Eleventy-SASS](https://www.npmjs.com/package/eleventy-sass) plug-in looks like a good one, and it appears to be well-documented.

# Creating the About Page

No use re-inventing anything, just have a look at the `Step 6 - Creating an About Page` portion of [How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) to learn how this is done.  

# Creating Posts - More Than Just a Page

Again, why re-invent anything?  Just have a look at the `Step 7 - Creating Posts` portion of [How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) to learn how this is done.  

Take note that you are NOT just creating a new page here, you're essentially creating a new "custom content type" called `posts`.  To learn about ways to extend this concept of "custom content types", or "collections", I recommend a couple of additional blog posts I found:  

  - [Eleventy Custom Content Type and Collection for Books](https://www.markllobrera.com/posts/eleventy-custom-content-type-and-collection-for-books/)  
  - [Eleventy Custom Content Type Collections/](https://www.joshcanhelp.com/eleventy-custom-content-type-collections/)  

# Filters  

One more time... Please have a look at the `Step 8 - Using Filters in Eleventy` portion of [How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) to learn about filters and how they tick.  

# Collections

I've given this section a title that's much different than you'll see in [How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) because the subject of `Collections` is that important!  So have a look at `Step 9 - Displaying Posts on the Homepage` for details, but pay close attention to all that goes on in our new `index.njk` file which now looks like this:

```html
---
title: Homepage
layout: layouts/base.njk
---

<section class="hero is-medium is-primary is-bold">
  <div class="hero-body">
    <div class="container">
      <h1 class="title">{{ site.title }}</h1>
      <h2 class="subtitle">{{ site.description }}</h2>
    </div>
  </div>
</section>

<section class="postlist mt-3 pt-3">
  <div class="container">
    <h2 class="title has-text-centered mt-3 mb-6">Recent posts</h2>
    <div class="columns">
      {% for post in collections.post | reverse %}   
        {% if loop.index0 < 3 %}
          <div class="column">
            <div class="card">
              <header class="card-header">
                <p class="card-header-title">
                  {{ post.data.title }}
                </p>
              </header>
              <div class="card-content">
                <div class="content">
                  {{ post.data.description }}
                </div>
              </div>
              <footer class="card-footer">
                <a href="{{ post.url }}" class="button is-fullwidth is-link card-footer-item">Read article</a>
              </footer>
            </div>
          </div>
          {% endif %}
      {% endfor %}
    </div>
  </div>
</section>
```

# Wrapping This Up

[How to Create and Deploy Your First Eleventy Website](https://www.digitalocean.com/community/tutorials/how-to-create-and-deploy-your-first-eleventy-website) goes on in steps 10 and 11 to save everything created here in a _GitHub_ repo (Step 10), and then deploy the blog as a static web app/site on _DigitalOcean_ (Step 11).  I've already completed the equivalent of Step 10 and you can find this project, and this `README.md` file at https://github.com/SummittDweller/eleventy-blog.  That's where I'm going to end this project, but my plan is to create a new blog, very similar to this one and using the process documented here to get me started.  Look for that project at https://github.com/SummittDweller/my-eleventy-blog.  

This `README.md` file is likely to become the first `post` in [my-eleventy-blog](https://github.com/SummittDweller/my-eleventy-blog).  

Rather than deploying [my-eleventy-blog](https://github.com/SummittDweller/my-eleventy-blog) to _DigitalOcean_, I'll probably follow the guidance from [Deploying an 11ty Site to Azure Static Web Apps](https://squalr.us/2021/05/deploying-an-11ty-site-to-azure-static-web-apps/) to host it on _Azure_.   I've used both hosts in the past, and I've been with _DigitalOcean_ much longer, but I still have some room for another "free" static app with _Azure_, so that's where I'm headed with this for now.   

Wish me luck!  