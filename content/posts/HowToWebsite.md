---
title: "How to create and host a website on the cheap"
date: 2023-01-15T00:42:16-04:00
draft: false
---

A guide for gamedevs to create professional looking website that are highly customizable and can be easily scaled out for features.

Oh hey, [you can look at ours as an example](https://rbagame.com)

## TLDR

### The Problem

Many website builders, while easy to build, are financially costly. But building a website from scratch has a high effort cost.

### Solution

Use a static website generator like [Hugo](https://gohugo.io/) hosted on [GitHub Pages](https://pages.github.com/) for a no financial and low effort cost website.

## Prerequisites

0. Some level of understanding of [git](https://git-scm.com/doc) and [GitHub](https://github.com/)
0. Some level of understanding of [html](https://www.w3schools.com/html/) and [css](https://www.w3schools.com/css/)
0. Knowledge of [Markdown](https://www.markdownguide.org/)
0. Comfort around running commands from cmd or terminal

## Hugo

[Hugo](https://gohugo.io/) is a static site generator. Hugo allows the developer to write website content in (easy to write and understand) Markdown files then converts that content into static html and css. Static in this sense means we lost the ability to create server side scripts or processes. For most gamedevs promoting their game, this is a completely reasonable trade off.

### Setup

The best way to get started with Hugo is to follow their own [Quick Start Guide](https://gohugo.io/getting-started/quick-start/). After following this guide, you will have Hugo and Git installed locally. You will also be familiar with how to run the basic Hugo commands to generate files for a website

### Themes

During the Quick Start guide there was a step for adding a [Hugo Theme](https://themes.gohugo.io/). This is an important step because this is how we can create a professional looking website at a pretty low effort cost. You can browse themes [here](https://themes.gohugo.io/). Find one that you like and install it following the instructions on the theme page. [Like this one for example](https://themes.gohugo.io/themes/reveal-hugo/#get-the-reveal-hugo-theme).

The great thing about Hugo is we can just use a theme as is or we can edit and add to the theme over time. Just make sure the theme you want to edit has a license that allows for it! Most of the themes have a MIT License, which is fine to edit and build on. Editing Hugo themes does require some level of knowledge in html and css. Don't know it? That's fine, just leave the theme as is! That's the great thing about building a site with Hugo. The theme on our website is based on [beautifulhugo](https://github.com/halogenica/beautifulhugo).

## GitHub

[GitHub](https://github.com/) is a website that allows devs to store and manager code with the source control tool [git](https://git-scm.com/doc). If you aren't using version control, even if you are a solo dev, this is my plea for you to start. They also have a pretty cool feature, called [GitHub Pages](https://pages.github.com/), that allows a GitHub repo to host a website _for free_. The catch? It will only host client side static web files, ie html, css, js. 

Oh how convenient, because Hugo only produces those client side static web files.

### Creating The Repo

[GitHub Pages](https://pages.github.com/) has its own quick start guide. Following this will generate a basic "hello world" html website. The website can be viewed at `https://{{your-github-username}}.github.io`. By default, GitHub will serve the website from the base directory. Serving from the base directory means we can't place our Hugo project into this repo. But we can change some settings so that this repo both stores the Hugo project and serves the static web files.

### Add Hugo to our git repo

Inside our newly created git repo, you can either create a new Hugo website or just copy and paste one that you have already created. Your directory structure will look something like this

```
my-hugo-project
 | archtypes/
 | content/
 | data/
 | layouts/
 | public/
 | static/
 | themes/
 | config.toml
```

After building our website with the command `$ hugo`, our static web files are generated and stored in the `public` folder. So that is the folder we want GitHub to host our website through. Push any changes up, and let us take a look at our website repo settings.

![GitHub Settings](/howtowebsite/settings.PNG)

then navigate to the Pages sub setting and update the directory where pages gets built from. For us, we serve it from `docs/`. If you didn't change any Hugo settings you can select `public/`.

![GitHub Settings](/howtowebsite/pages.PNG).

And that's it. Give GitHub some time to correctly route to your new website. But that is it.

The last thing we can do is change the [domain name](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site). This does require you to buy a domain name.

## Workflow

Now that everything is connected and configure, all we have to do is add Markdown content under the `content/` folder then build the website using `$ hugo` command. We then push all of our local code to GitHub where GitHub pages deploys and hosts our website.