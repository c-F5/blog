---
title: "Deploy a Hugo Site with Cloudflare Pages and GitHub"
description: "How to deploy a Hugo Site with Cloudflare Pages and GitHub for free!"
date: 2023-03-23
draft: false
tags: ["Cloudflare Pages", "Hugo", "Static Site","Cloudflare", "GitHub"]
---

In this guide I'm going to explain how to host your [Hugo](https://gohugo.io/) Static Site using [Cloudflare Pages](https://pages.cloudflare.com/) and [GitHub](https://github.com/) for free.

Feel free to use the Table of Contents above to skip ahead.

## Introduction

In a previous blog post ["Building a Hugo Static Site"](/blog/23-02-23-hugo-static-site) I explained how to use [Hugo](https://gohugo.io/) to create a Static Website.

In this guide I'm going to explain how I use [Cloudflare Pages](https://pages.cloudflare.com/) and [GitHub](https://github.com/) to host and deploy my [blog](/blog)

## Cloudflare Pages and GitHub

I explained in a [previous post](/blog/23-02-23-hugo-static-site/#cloudflare-pages-and-github), you can use hosting providers like [Cloudflare Pages](https://pages.cloudflare.com/) to generate your static site for you as part of their deployment process when deploying your site. This means you don't need to generate the site yourself every time you update/add new site content.

You put your [Hugo](https://gohugo.io/) site on [GitHub](https://github.com/) and tell [Cloudflare Pages](https://pages.cloudflare.com/) to use that GitHub repository when generating the site for you. When you then update/add new content to the site, you just upload the changes to the GitHub repository. Cloudflare then detects the change and regenerates the static site for you.

There are many hosting providers that do this, I chose [Cloudflare Pages](https://pages.cloudflare.com/) as I use Cloudflare as my [Domain registrar](https://www.cloudflare.com/products/registrar/) so it made sense to use them, plus their [free plan](https://developers.cloudflare.com/pages/platform/functions/pricing/#free-plan) was more than enough for my needs.

[Cloudflare](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/) have some really good documentation explaining how to deploy a Hugo Site with Cloudflare Pages, but I'll do a quick overview below.

## Push Hugo Site to GitHub

Before using [Cloudflare Pages](https://pages.cloudflare.com/) to deploy your Hugo Site. You need to put your Site on [GitHub](https://github.com/).

If you have never uploaded files/content to a GitHub repository before, there are a few ways explained [here](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)

I use [Visual Studio Code](https://code.visualstudio.com/) as well as [Git](https://git-scm.com/) to edit and upload my site to my GitHub repository.
There is a more [detailed guide here](https://code.visualstudio.com/docs/sourcecontrol/intro-to-git#:~:text=Publish%20local%20repository%20to%20GitHub&text=Use%20the%20Publish%20to%20GitHub,code%20to%20the%20remote%20repository).

A quick overview:
- Install Git and Visual Studio Code
- In Visual Studio Code open "Source Control" and login to your GitHub profile
- "Clone repository" to GitHub and select the "GitHub repository" you want to upload your site too
- You can then "commit and push" the site to your GitHub repository
- Go to your GitHub account and check your content is there in the right repository

{{< notice info >}}
Please make sure to read the detailed guides above. My steps above are just a quick overview.
{{< /notice >}}

## Deploy with Cloudflare

Now that the site is on GitHub we need to log in to Cloudflare, connect it to the GitHub repository and deploy the site.

- Log in to [Cloudflare](https://dash.cloudflare.com/login) with your account or sign up if you don't have one already
- Select 'Pages' on the left tab
- Create a "Project" and "Connect to Git"
- Log in to GitHub and authorize Cloudflare access
- Select the repository you want Cloudflare to deploy and begin setup
- Fill in the needed information
    - Give the Project a name
    - "Production Branch" set as `main`
    - "Framework preset" set to `Hugo`
    - Make sure "Build output directory" is set as `/public`
    - Expand **Environment variables** and "Add variable". In the "Variable name" enter `HUGO_VERSION` and under "Value" enter the version of Hugo you are currently using. I'm using `0.110.0`

    *I explain how to find out the version of Hugo you are using in the [Setting up Hugo](/blog/23-02-23-hugo-static-site/#setting-up-hugo) section of this [post](/blog/23-02-23-hugo-static-site/#setting-up-hugo).*

- Hit 'Save and Deploy'. Cloudflare will now start to build and deploy your site
- If all goes well you will get a confirmation message all was done.
- You should now have a unique subdomain that links to your site `projectname.pages.dev`

{{< notice warning >}}
It's really **important** to expand "Environment variables" and set the "Variable name" and "Value" above. If not you may get errors when trying to deploy
{{< /notice >}}


## Using a custom domain (Optional)

If you own your own domain and don't want to use the subdomain `*.pages.dev` Cloudflare assigns to your project. You can setup your own [custom domain or subdomain](https://developers.cloudflare.com/pages/platform/custom-domains/).

- On your project page select the project
- Under the project select "Custom domains"
- Select "Setup a custom domain"
- Enter your "custom domain" and follow the instructions

   

I hope you found this post useful.

Colin

---

*Also published on [Medium](https://medium.com/@cF5)*
