---
title: "Create a Theme"
date: 2018-07-05T00:09:11+10:00
draft: false
---

It is certainly not necessary to use or write your own theme. For this tutorial, if you choose not to use a theme, you will need to place the html template files under `layouts`. If creating a theme, place it under `themes/<THEME>/layouts/`.

E.g. `layouts/404.html`

```sh
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
│   └── 404.html               <-- HERE
├── static
└── themes
    └── <THEME>
        ├── archetypes
        ├── layouts
        │   ├── 404.html       <-- OR HERE
        │   ├── _default
        │...
        │   └── partials
        ├── LICENSE
        ├── static
        └── theme.toml

```

---

> Hugo currently doesn’t ship with a “default” theme. This decision is intentional. We leave it up to you to decide which theme best suits your Hugo project.

> -- [Hugo Docs](https://gohugo.io/themes/installing-and-using-themes/)

Let's make our own theme!

Go ahead and run `hugo new theme walkthrough`.

This will add a theme to the `themes` directory:

```sh
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
    └── walkthrough
        ├── archetypes
        │   └── default.md
        ├── layouts
        │   ├── 404.html
        │   ├── _default
        │   │   ├── baseof.html
        │   │   ├── list.html
        │   │   └── single.html
        │   ├── index.html
        │   └── partials
        │       ├── footer.html
        │       └── header.html
        ├── LICENSE
        ├── static
        │   ├── css
        │   └── js
        └── theme.toml

```

Don't forget to update the `theme.toml` file with the correct information.

Now we need to let Hugo know that we want to use this theme.

Go to your `config.toml` file and add this line:

```toml
theme = "walkthrough"
```

```
hugo server
```

Still nothing?!

---

Up next: We define an index page
