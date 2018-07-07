---
title: "Configuring Hugo"
date: 2018-07-04T00:09:11+10:00
draft: false
---

[Details@Docs](https://gohugo.io/getting-started/quick-start/): Hugo's Quick Start guide

## Install Hugo 

Simply follow the instructions on [the Hugo Documentation site](https://gohugo.io/getting-started/installing/) to get Hugo up and running on your system.

Run `hugo new site mysite` 

Navigate to `mysite` and run `hugo server`

[Details@Docs](https://gohugo.io/commands/hugo_server/): What is `hugo server`?

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

---

Let's take a look at the `config.toml` file that was generated for us:

```toml
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"

```

This `config` file is where we configure our Hugo site. [The docs](https://gohugo.io/getting-started/configuration/#all-configuration-settings) has a list of all Hugo-defined variables that are available.

When we are ready to publish our Hugo site, we need to make sure that `baseURL` is filled with the correct domain.

We can also define our own custom variables that we can access in our templates. Read more about that [here](https://gohugo.io/variables/site/#the-site-params-variable).


There are 230+ themes available on the [Hugo Themes](https://themes.gohugo.io) site. We could of course choose to use one of those, but for this tutorial we are making our own.

---

Up next: We create our own theme
