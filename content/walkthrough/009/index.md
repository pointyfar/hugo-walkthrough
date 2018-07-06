---
title: "Define Baseof"
date: 2018-07-05T00:59:16+10:00
draft: false
---

You may have noticed when we first generated a new theme that it came with a `baseof.html` page. 

[Details@Docs](https://gohugo.io/templates/base/#define-the-base-template): What is a baseof template?

> As a default template, it is the shell from which all your pages will be rendered ...

> -- [Hugo Docs](https://gohugo.io/templates/base/#define-the-base-template)

```bash
...
├── layouts
│   ├── 404.html
│   ├── _default
│   │   ├── baseof.html               <-- THIS ONE
│   │   ├── list.html
│   │   └── single.html
│   ├── index.html
...
```
Let's separate the 'main' part of the HTML from the 'base' part.

```html
<!-- baseof.html -->
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

We define a `main` block which we can overwrite in our templates. We can then redefine our `list.html` template as follows:

```html 
{{ define "main" }}
  <main>
    <div>
     <h1>{{ .Title }}</h1>
        <ul>
          {{ range .Data.Pages }}
            <li><a href="{{.Permalink}}">{{.Title}}</a></li>
          {{ end }}
        </ul>
    </div>
  </main>
{{ end }}
```

What happens if we don't override the main block? Let's try that on our `single.html` template:

```html 
{{ define "main" }}
{{ end }}
```

{{% img rsc="images/009-main-block-source.png" alt="Screenshot" %}}

Let's do it properly now:

```html 
{{ define "main" }}
  <section id="main">
    <h1 id="title">{{ .Title }}</h1>
    <div>
      <article id="content">
        {{ .Content }}
      </article>
    </div>
  </section>
  <aside id="meta">
    <div>
      <section>
        <h4 id="date"> {{ .Date.Format "Mon Jan 2, 2006" }} </h4>
        <h5 id="wordcount"> {{ .WordCount }} Words </h5>
      </section>
      {{ with .Params.topics }}
      <ul id="topics">
        {{ range . }}
          <li><a href="{{ "topics" | absURL}}/{{ . | urlize }}">{{ . }}</a></li>
        {{ end }}
      </ul>
      {{ end }}
      {{ with .Params.tags }}
      <ul id="tags">
        {{ range . }}
        <li> <a href="{{ "tags" | absURL }}{{ . | urlize }}">{{ . }}</a></li>
        {{ end }}
      </ul>
      {{ end }}
    </div>
    <div>
      {{ with .PrevInSection }}
      <a class="previous" href="{{.Permalink}}"> {{.Title}}</a>
      {{ end }}
      {{ with .NextInSection }}
      <a class="next" href="{{.Permalink}}"> {{.Title}}</a>
      {{ end }}
    </div>
  </aside>
{{ end }}
```

{{% img rsc="images/009-single-page-main.png" alt="Screenshot" %}}

---

Up next: We define partials.