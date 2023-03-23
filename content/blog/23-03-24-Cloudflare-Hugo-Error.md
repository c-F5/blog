---
title: "Cloudflare Pages Error ''function 'warf' not defined'' FIXED"
description: "Cloudflare Pages fails to deploy Hugo Site FIXED"
date: 2023-03-24
draft: false
tags: ["Cloudflare Pages", "Hugo","Cloudflare"]
---

## Cloudflare Pages fails to deploy Hugo Site

**Error: "/opt/buildhome/repo/themes/PaperMod/layouts/shortcodes/collapse.html:3:1": parse failed: template: shortcodes/collapse.html:3: function "warnf" not defined**

In a [previous post](/blog/23-03-23-cloudflare-github/) I explained how to use [Cloudflare Pages and GitHub to deploy a Hugo Static Site](/blog/23-03-23-cloudflare-github/).

In this post I [explained how important](/blog/23-03-23-cloudflare-github/#deploy-with-cloudflare) it was to expand "Environment variables" and set the "Variable name" as `HUGO_VERSION` and "Value" as the version of Hugo you want Cloudflare to use, otherwise you may get an error.

Below is the error I was getting when I first tried to deploy without setting the values

![Error](/blog/23-03-24-cloudflare-hugo-error/error.jpg)

The way to fix this error is to specify the "Variable name" and "Value" (version of Hugo you want to use) 

![Settings](/blog/23-03-24-cloudflare-hugo-error/settings.jpg)






Colin

---

*Also published on [Medium](https://medium.com/@cF5)*