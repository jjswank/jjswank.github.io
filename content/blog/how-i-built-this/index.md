---
title: How I Built This
date: "2022-05-02T22:12:03.284Z"
description: "Hello World personal blog with GatsbyJS"
---

When looking to build a personal blog I decided to go with GatsbyJS for a couple reasons:

* **Cost**: This site is served as static content from a CDN so there is very little cost to hosting. I only have to pay for the amount of traffic I receive. There is no cost to idle servers. With github pages, there is not cost of hosting.

* **Availability**: Because this site is just static files served from a CDN there are no backend servers to worry about going down in the middle of the night.

* **Performance**: Becuase pages are not dynamically rendered the site renders quickly. The site renders quickly if there is 1 view or 1 million views.

# How it works

GatsbyJS follows a JAM stack achritecture. Instead of dynamically rendering pages everytime they are requested the pages a pre-rendered up front into a static page. Whenever the page is changed it wil be rerendered. This is great for SEO bacause search engines can read the pages easier. 

The trade off is between speed of rendering vs speed to applying changes. In my case because page updates are made much less than pages are views, it makes much more sense to prioritize speed of rendering.

# Hosting

The site is hosted using github pages. Therefore there is no hosting cost to me. Github host the site from a git repository.

# Getting Started

1. Create a new gatsby project using the gatsby-starter-blog template. This contains a basic blog with all the features needed to get started.

```
npx gatsby new <YOUR_GITHUB_USERNAME>.github.io https://github.com/gatsbyjs/gatsby-starter-blog
```

To run the blog locally run:
```
npx gatsby develop
```
Blog pages are stored as markdown files in `content\blog`. While developing, any changes will hot reload. To add a blog post, add a new folder to the `content\blog` directory with an index.md file. Save the file and view the changes at http://localhost:8000


2. Install the `gh-pages` package which will handle publishing the built production app to a seperate branch which will be served as the github page.
```
npm install gh-pages --save-dev
```
In your `package.json` add the following deployment script:
```
"deploy": "gatsby build && gh-pages -d public -f"
```
This will build a production version of the app with all the static assets generatde in a folder called `public`. Then it will take the contents of the public folder and push it to a branch in github called `gh-pages`. To manually deploy the site run:
```
npm run deploy
```

3. To set up the git repository, create a new repository with the name `<YOUR_GITHUB_USERNAME>.github.io` and follow the instructions to push your app to the repo on the main branch.

To enable github pages, fo the repository settings, selecte pages, and change the source branch to gh-pages. Once you save and deploy the site you should see the blog hosted at <YOUR_GITHUB_USERNAME>.github.io

# Up Next

I'd like to automate the deploys any time a commit is merged into the main branch. I'd also like to add a wysiwyg editor to replace manually editing the markdown files.