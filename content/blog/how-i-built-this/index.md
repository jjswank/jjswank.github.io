---
title: How I Built This
date: "2022-05-02T22:12:03.284Z"
description: "Hello World personal blog with GatsbyJS"
---

When looking to build a personal blog I decided to go with GatsbyJS for a couple reasons:

Cost: This site is served as static content from a CDN so there is very little cost to hosting. I only have to pay for the amount of traffic I receive. There is no cost to idle servers.

Availability: Because this site is just static files served from a CDN there are no backend servers to worry about going down in the middle of the night.

Performance: Becuase pages are not dynamically rendered the site renders quickly. The site renders quickly if there is 1 view or 1 million views.

How it works

GatsbyJS follows a JAM stack achritecture. Instead of dynamically rendering pages everytime they are requested the pages a pre-rendered up front into a static page. Whenever the page is changed it wil be rerendered. This is great for SEO bacause search engines can read the pages easier. The trade of is between speed of rendering vs speed to applying changes. In my case because page updates are made much less than pages are views, it makes much more sense to prioritize speed of rendering.

Hosting

The site is hosted using github pages. Therefore there is no hosting cost to me. Github host the site from a git repository.