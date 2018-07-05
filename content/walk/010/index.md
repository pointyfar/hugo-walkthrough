---
title: "Define Partials"
date: 2018-07-05T01:00:57+10:00
draft: false
---

Let's go one step further and split off the code in `baseof.html` into partials.

[Details@Docs](https://gohugo.io/templates/partials/)

```html
<!-- layouts/_default/baseof.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{.Site.Title}}</title>
  </head>
  <body>
    {{ block "main" . }}
      <!-- this is the main block -->
      Main Block
    {{ end }}
  </body>
</html>
```

We can split off the head and put it into a partial:

```html
<!-- layouts/partials/header.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{.Site.Title}}</title>
  </head>
  <body>
```
as well as the foot:

```html
<!-- layouts/partials/footer.html -->
</body>
</html>
```

And we are left with our `baseof.html` looking like this:


```html
<!-- layouts/_default/baseof.html -->
{{ partial "header.html" . }}
{{ block "main" . }}
{{ end }}
{{ partial "footer.html" . }}

```
