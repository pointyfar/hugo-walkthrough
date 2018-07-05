---
title: "Getting Started"
date: 2018-07-04T23:49:56+10:00
draft: false
---

So you want a [static site](https://gohugo.io/about/benefits/) and have [decided to use Hugo](https://www.linode.com/docs/websites/static-sites/how-to-choose-static-site-generator/). What next?

We make a Hugo site!

# Making a Hugo Site: A Walkthrough 

This tutorial series aims to walk you through the basics of how to make a website with Hugo. No fancy JavaScript, not a lot of CSS, just enough HTML to make things work. This is intended to be a complement to the excellent [official Hugo documentation](https://gohugo.io/) (which you really should go read) which will frequently be referenced throughout the tutorial.

## Why write yet another Hugo tutorial?

Yes, there are plenty of other guides and tutorials out there, better written and by people smarter than myself. I have personally found though that most of them are either too basic, simple `Hello World` examples, which don't go to enough depth, or too complicated for a first-time Hugo adventurer.

## What this walkthrough DOES NOT cover

* How to write HTML/CSS/JS code
* How to `git`
* How to deploy your site
* How to configure a different theme
* Why your Hugo site isn't working

---

Enough of the chatter, show me the code!

## Install Hugo 

Simply follow the instructions on [the Hugo Documentation site](https://gohugo.io/getting-started/installing/) to get Hugo up and running on your system.

Run `hugo new site mysite` 

Navigate to `mysite` and run `hugo server`

[Details@Docs](https://gohugo.io/commands/hugo_server/)

```sh
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
```

Open your browser and navigate to http://localhost:1313/ and you should see a Hugo website!

{{% img rsc="images/001-empty.png" alt="Screenshot" %}}

... or not.

We have a few things we need to put together before we get an actual website running.