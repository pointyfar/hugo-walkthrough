---
title: "Prettify"
date: 2018-07-05T11:07:58+10:00
draft: false
---

Before we go any further, let's quickly add some styles to our page and remove the borders we previously defined inline.

We can put assets such as `css`, `js`, `img` files into the `static` folder.

[Details@Docs](https://gohugo.io/content-management/static-files/)

```bash
.
├── content
│...
├── layouts
├── static              <-- HERE
└── themes
    └── <THEME>
        │...
        ├── static      <-- HERE
        │   ├── css
        │   └── js
        └── theme.toml
```

The `static` directory maps to `/`. That means that if you have your website on `http://example.com/`, `static/css/styles.css` will be in `http://example.com/css/styles.css`

Let's create our own `styles.css` and put it in `static/css`:

```css
section {
  padding: 2rem 5rem;
}
```

and of course add a reference to it in the `head`:

```html 
<!-- themes/<THEME>/layouts/partials/header.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{.Site.Title}}</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://unpkg.com/picnic">
    <link rel="stylesheet" href="{{.Site.BaseURL}}css/styles.css">
    
  </head>
  <body>
```
*I am using [picnic.css](https://picnicss.com/) from a CDN as a base style but feel free to use your preferred styles.*

{{% img rsc="images/012-no-styles.png" alt="Before" %}}

{{% img rsc="images/012-with-styles.png" alt="After" %}}


I am also adding a few style classes to the templates. These are purely aesthetic and optional.

```html
<!-- layouts/_default/summary.html -->
<div class="card">
  <h4><a href="{{.Permalink}}">{{ .Title }}</a></h4>
  <h6>{{ .WordCount }} words written on {{ .Date }}</h6>
  {{ .Summary }}
</div>
```

```html 
<!-- layouts/_default/single.html -->
<div class="flex two">
  <div>
  {{ with .PrevInSection }}
    <a class="button previous" href="{{.Permalink}}">Previous</a>{{.Title}}
  {{ end }}
  </div>
  <div>
  {{ with .NextInSection }}
    <a class="button next" href="{{.Permalink}}">Next</a>{{.Title}}
  {{ end }}
  </div>
</div>
```

{{% img rsc="images/012-buttons.png" alt="Aesthetics" %}}

Let's add a navbar with our logo that shows in every page.


```html 
<!-- layouts/partials/header.html -->
<!DOCTYPE html>
<html lang="en">
  <head>...</head>
  <body>
    
  <nav>
    <a href="{{.Site.BaseURL}}" class="brand">
      <img class="logo" src="{{.Site.BaseURL}}my-logo-placeholder-fit.png">
      <span>{{ .Site.Title }}</span>
    </a>
  </nav>
```

```sh
.
├── archetypes
├── config.toml
├── content
├── data
├── layouts
├── static
│   └── my-logo-placeholder-fit.png
└── themes

```

{{% img rsc="images/012-navbar.png" alt="Navbar" %}}
