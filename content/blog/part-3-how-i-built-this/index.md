---
title: "Part 3: How I Built This"
date: 2022-05-04T00:36:58.020Z
description: Adding a CMS for updating blog content
---
The goal of this project is to add a CMS for editing blog posts without having to run the application locally and make git commits. This entire blog post was written and published doing exactly that. 

To accomplish this I chose Netlify CMS. It provides a UI for editing the blog content. There is no backend. When the blog posts are saved, Netlify CMS makes a commit directly to github, triggering a new build to publish the changes.

# Getting Started

1. The first step is to add the netlify cms app and plugin to your application:

```
npm install --save netlify-cms-app gatsby-plugin-netlify-cms
```

2. Next create a new file called `static/admin/config.yml` to configure the cms application. Add in the following text:

```
backend:
  name: github
  repo: <GITHUB_USERNAME>/<GITHUB_REPO_NAME>
  branch: main

media_folder: static/img
public_folder: /img

collections:
  - name: 'blog'
    label: 'Blog'
    folder: 'content/blog'
    create: true
    slug: 'index'
    media_folder: ''
    public_folder: ''
    path: '{{title}}/index'
    editor:
      preview: false
    fields:
      - { label: 'Title', name: 'title', widget: 'string' }
      - { label: 'Publish Date', name: 'date', widget: 'datetime' }
      - { label: 'Description', name: 'description', widget: 'string' }
      - { label: 'Body', name: 'body', widget: 'markdown' }
```

3. In the `gatsby-config.js` file you need to add `gatsby-plugin-netlify-cms` to the plugins array. This will add the `/admin` endpoint to your application to access the CMS.
4. Lastly you will need to configure netlify to handle the authentication. This requires creating a netlify account and creating a netlify site. This can be done for free. For more information in this see the [Netlify documentation](https://docs.netlify.com/visitor-access/git-gateway/)

# Thats It

Once you push your changes you should be able to access the `/admin` endpoint and login with github. From there you can edit and create new blog posts. This entire blog post was made without pulling or running the application locally.