---
title: "Define Index"
date: 2018-07-05T00:11:15+10:00
draft: false
---

Opening up `themes/walkthrough/index.html`, we see...

Nothing. 

That explains it!

Let's go add some content to it:

```html
<!-- themes/walkthrough/index.html -->
<!DOCTYPE html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>My First Hugo Site</title>
</head>

<body>
  Hello World!
</body>
</html>
```

{{% img rsc="images/003-hello-world.png" alt="Screenshot" %}}

Yay!

But that's just HTML, isn't it? Let's use some Hugo magic!

[Details@Docs](https://gohugo.io/templates/introduction/): What are Hugo templates?

```html
<!-- layouts/index.html -->
<!DOCTYPE html>

<html lang="en">
<head>
  <meta charset="utf-8">
  <title>{{.Site.Title}}</title>
</head>

<body>
  {{.Site.Title}}
</body>
</html>
```

{{% img rsc="images/003-site-title.png" alt="Screenshot" %}}

Cool! But where does this value come from?

```toml
# config.toml
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"              # <-- HERE!!

theme = "walkthrough"
```

Change the value for title and see the changes:

```toml
title = "My New Hugo Site That I Built Myself"
```

{{% img rsc="images/003-site-title-changed.png" alt="Screenshot" %}}


(You may need to restart `hugo server` when changing `config.toml`)

---

Up next: We write some content.