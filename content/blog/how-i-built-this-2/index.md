---
title: "Part 2: How I Built This"
date: "2022-05-02T23:12:03.284Z"
description: "Automating the publishing of changes"
---

Instead of relying on manual deploys to publish changes to the blog I wanted to automate this work eveytime a merge is made to main. To do this I created a github action that runs on merges.

# Getting started

1. Create a file in your repository called `.github\workflows\build-and-deploy.yml`:

```
name: build-and-deploy

on:
  push:
    branches:
      - main
jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '14'
      - run: npm install
      - run: npm run build
      - run: |
          git remote set-url origin https://git:${GITHUB_TOKEN}@github.com/${GITHUB_REPOSITORY}.git
          npx gh-pages -d public -u "github-actions-bot <support+actions@github.com>"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
This creates a new github action that runs whenever there is a merge to the main branch. It will build the production version of the application and push it to the gh-pages branch automatically.

2. Commit and push the change up to your repository. Github should automatically detect the file and create a new action. 


![Github Actions Page](./github-actions.jpg)

Clicking through you can see the completed job steps as they run:

![Github Actions Page](./github-actions-2.jpg)

Thats it. Now whenever a change or blog post is commited to the main branch, the site will rebuild and deploy.