---
title: "Building a Hugo Static Site"
description: "A simple guide showing you how to use Hugo for a static site"
date: 2023-02-23
draft: false
tags: ["Hugo", "Static Site","Cloudflare", "Git", "GitHub", "Go"]
---

In this guide I'm going to explain why I decided to use [Hugo](https://gohugo.io/) for my blog and cover the process of setting up a simple static site.

Feel free to use the Table of Contents above to skip ahead.

## Why I decided on a Hugo Static Site

When I decided to create a blog, I started looking around at all the different options. Should I just use [WordPress](https://wordpress.com/free/), [Weebly](https://www.weebly.com/uk), [Wix](https://www.wix.com/) or one of the many other dynamic sites?

I then came across static sites and started to read into them a bit more, reading the benefits of using them over dynamic sites.
Static sites are as it sounds, they are "static" or "fixed". Once the site had been written it stays the same and displays the same content to every site visitor. Some of the main benefits of using a static site are they are **fast, flexible and secure**.

You can read a more in-depth description from [this blog](https://www.sanity.io/static-websites)

The only problem I found using a static site, is that if you update something or add a new page, you may also have to update every other page manually. This could be a **pain** and **time consuming**.

This is where a static site generator (SSG) comes in. They generate a fully static HTML website from the information and theme you provide. So, if you add a new page you then use the SSG to generate a new site, all the pages are updated without you having to manually update each page.  Making the process so much easier.
[Cloudflare](https://www.cloudflare.com/learning/performance/static-site-generator/) explains this in more detail.

With this information and me liking a challenge I decided to give a static site a go.

My next challenge was to find a SSG to use and find a theme that I liked. I mainly focused on [Hugo](https://gohugo.io) and [Jekyll](https://jekyllrb.com/) but there are many [more](https://jamstack.org/generators/).

I decided on [Hugo](https://gohugo.io), mainly because it was so easy to setup and there were more templates I liked the look of. I then decided to use the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) Theme, as it seemed to tick all the things I wanted for the blog.

## Prerequisites for setting up Hugo

Although not needed, it is recommended to install both [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) and [Go](https://go.dev/doc/install) when working with Hugo.

More information about these [prerequisites](https://gohugo.io/installation/windows/#prerequisites) can be found on the [Hugo site](https://gohugo.io/installation/windows/#prerequisites).

## Setting up Hugo

Firstly as I'd never used Hugo before I needed to setup the environment to run Hugo on my computer

{{< notice info >}}
This part only needs to be done if you have never used Hugo before or are using Hugo on a new computer.  If you have Hugo already installed on your computer you can leave this section out.
{{< /notice >}}

I am using Windows on my computer so this part is only relevent if you are running Windows too.  If you are running a different operating system, Hugo provides [installation instructions](https://gohugo.io/installation/) for these as well. These include [macOS](https://gohugo.io/installation/macos/), [Linux](https://gohugo.io/installation/linux/), [Windows](https://gohugo.io/installation/windows/) (Which I'm using) and [BSD](https://gohugo.io/installation/bsd/).

- First a folder needs to be created to install Hugo and to store the sites.
- Create a new folder, something like `C:\Hugo` as well as two subfolders `C:\Hugo\Sites` and `C:\Hugo\Bin`
You can install Hugo using a selection of [package managers](https://gohugo.io/installation/windows/#package-managers) or their [Prebuilt binaries](https://gohugo.io/installation/windows/#prebuilt-binaries). I decided to use their Prebuilt binaries.
- Go to the [Prebuilt binaries](https://gohugo.io/installation/windows/#prebuilt-binaries) section or the [latest release](https://github.com/gohugoio/hugo/releases/latest) page on GitHub and download the latest release. I highly recommend you download the extended version. The latest version for me was `hugo_extended_0.110.0_windows-amd64.zip`
- Now go and extract the .zip file into `C:\Hugo\Bin`.
- We now need to add the Hugo directory to the PATH environment variable.
    - To do this go this open the start menu and search for *environment variable* and choose *Edit the environment variables*.
    - Select *Environment Variables*
    - Select *Path* under the User variables and select *edit*
    - In the *Edit environmental variables* window select *New* and enter the path we just extracted the .zip folder to `C:\Hugo\Bin`.
    - Select *OK* and apply the changes.
- Open up a terminal or command prompt window and enter *hugo version* to check the version is correct and it's installed successfully.
```console
C:\Hugo>hugo version
```
Hugo has now been installed successfully.

Now into creating the actual site.

## Creating a new Hugo Site and applying a theme

Firstly we will create a new site and then apply a sample theme.

{{< notice info >}}
This section only needs to be done if you are creating a new site. If you already have a site created, you can skip this section.
{{< /notice >}}

- Open terminal and navigate to the folder we just created.
```console
C:\>cd Hugo\Sites
```
- Next we need to tell Hugo to create a new site.
```console
C:\Hugo\Sites>hugo new site <SiteName>
```
Change "SiteName" to the name of the site.

The Basic website has now been created, it's time to apply a theme.

A theme will change the look and style of the website to suit your needs. There any many themes for you to choose from. Hugo has a large selection to choose from here: [https://themes.gohugo.io/](https://themes.gohugo.io/).

Each theme should have instructions on how to apply the theme and may also have a demo link so you are able to see a live version of it.
Many of them have very in-depth documentation explaining all the functions available when using the selected theme.

I'm going to use the [PaperMod](https://themes.gohugo.io/themes/hugo-papermod/) theme, also found on [GitHub](https://github.com/adityatelange/hugo-PaperMod).

There are three methods for installing this theme, I'm going to use method one, the other two methods can be found on the [theme wiki](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation)

- Open terminal if you still haven't got it open and navigate to the folder site
```console
C:\>cd Hugo\Sites\SiteName
```
- You then want to clone the theme into your site you've just created
```console
C:\Hugo\Sites\SiteName> git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```
This grabs the site from GitHub and clones it into themes/PaperMod
- In future if you want to update the theme, you navigate to the theme and run "git pull"
```console
C:\Hugo\Sites\SiteName> cd themes\PaperMod
C:\Hugo\Sites\SiteName\themes\PaperMod> git pull
```

Now we need to edit the config file in the root folder to tell it to use the installed theme.
- Open the config file in your chosen editor (I use [Visual Studio Code](https://code.visualstudio.com/)) and add the line

`theme: "PaperMod"`

- Save the file

## Run the Hugo Server

Now it times to see your new site running on your local machine.

- Open terminal and navigate to the folder site
```console
C:\>cd Hugo\Sites\SiteName
```
- Start the Hugo server
```console
C:\Hugo\Sites\SiteName> hugo server -D
```
This will start the server locally on your local machine and allow you to browse to it using your browser
- Navigate to the site shown in your terminal window.  This is usually `http://localhost:1313`

There is your site running.

You can now make changes to the site. You can edit the config file to change the site settings. Here is a [sample config](https://github.com/adityatelange/hugo-PaperMod/wiki/Installation#sample-configyml) file for the theme I installed. You can also start to add some [site content](https://gohugo.io/getting-started/quick-start/#add-content).

{{< notice note >}}
I will be covering adding [site content](https://gohugo.io/getting-started/quick-start/#add-content) and other things in a seperate blog post soon.
{{< /notice >}}

When editing and making changes to the site, as long as you are still running `hugo server -D` in the terminal, all the changes will be refreshed in the browser. Meaning you can see any changes you make instantly.

## Generating the Static Site with Hugo

When you are happy with the look, feel and content on the site it's time to generate the **static** version of the site for you to deploy.

When you publish the site, Hugo creates the full static site in the `public` folder. This is the folder that you will use when you deploy the site.

- To generate the site, you simply navigate to the site folder and tell Hugo to generate with the command `hugo`
```console
C:\Hugo\Sites\SiteName> Hugo
```
The `public` folder will have been created with all the static files needed to deploy your new site.

## Cloudflare Pages and GitHub

You can also use hosting providers like [Cloudflare Pages](https://pages.cloudflare.com/) to generate the static site for you as part of their deployment process when deploying your site. This means you don't need to generate the site yourself every time you update/add new site content.

You can put your Hugo site on [GitHub](https://github.com/) and tell [Cloudflare Pages](https://pages.cloudflare.com/) to use the GitHub repository to generate the site for you. When you then update/add new content to the Git Hub repository Cloudflare detects the change and regenerates the static site for you.

{{< notice note >}}
I will be covering how to do this in another blog post.

**Using [Cloudflare Pages](https://pages.cloudflare.com/) and [GitHub](https://github.com/) to host your static website.**
{{< /notice >}}

[Cloudflare](https://developers.cloudflare.com/pages/framework-guides/deploy-a-hugo-site/) have some good documentation explaining how to a Hugo Site with Cloudflare Pages.

I hope you found this post useful.

Colin
