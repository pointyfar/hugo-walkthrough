---
title: "Define Single Page"
date: 2018-07-05T00:53:13+10:00
draft: false
---

Let's modify the code before to include a link to the actual pages

```html 
<!-- layouts/_default/summary.html -->
<div style="border:1px solid blue; margin:2px">
  <h4><a href="{{.Permalink}}">{{ .Title }}</a></h4>
  <h6>{{ .WordCount }} words written on {{ .Date }}</h6>
  
  {{ .Summary }}
</div>
```

and navigate to one of them: 

{{% img rsc="images/006-single-page-404.png" alt="Screenshot" %}}

Can you guess what's going on here?

Well, our `layouts/_default/single.html` is empty. This is what Hugo uses to render single pages.

[Details@Docs](https://gohugo.io/templates/single-page-templates/): What are single templates?

So let's put something in there!

Using an example based on the sample template in the [docs](https://gohugo.io/templates/single-page-templates/):

```html
<!-- layouts/_default/single.html -->
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{.Site.Title}}</title>
  </head>
  <body>
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
        <div>
          <h4 id="date"> {{ .Date.Format "Mon Jan 2, 2006" }} </h4>
          <h5 id="wordcount"> {{ .WordCount }} Words </h5>
        </div>
        {{ with .Params.topics }}
        <ul id="topics">
          {{ range . }}
            <li><a href="{{ " topics " | absURL}}{{ . | urlize }}">{{ . }}</a> </li>
          {{ end }}
        </ul>
        {{ end }}
        {{ with .Params.tags }}
        <ul id="tags">
          {{ range . }}
          <li> <a href="{{ " tags " | absURL }}{{ . | urlize }}">{{ . }}</a></li>
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
  </body>

</html>

```

{{% img rsc="images/006-single-page.png" alt="Screenshot" %}}

Now let's break this down.

The first `<section>` block you are already familiar with: `{{.Title}}` is just the post's `title` as defined in its frontmatter, and the `{{.Content}}` the main text.

---

```
<h4 id="date"> {{ .Date.Format "Mon Jan 2, 2006" }} </h4>
```

Read up [here](https://gohugo.io/functions/format/) to find out more about Go/Hugo's date formatting.

---


```html 
<div>
  {{ with .PrevInSection }}
  <a class="previous" href="{{.Permalink}}"> {{.Title}}</a>
  {{ end }}
  {{ with .NextInSection }}
  <a class="next" href="{{.Permalink}}"> {{.Title}}</a>
  {{ end }}
</div>
```

`.PrevInSection` and `.NextInSection` are [page variables](https://gohugo.io/variables/page/#page-variables) which point to the previous and next content in the same section, respectively. 

`.Prev` and `.Next` are also available, which point to the previous and next content regardless of its section.

---

```html
{{ with .Params.topics }}
<ul id="topics">
  {{ range . }}
    <li><a href="{{ "topics" | absURL}}{{ . | urlize }}">{{ . }}</a></li>
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
```

We can include pre-defined as well as custom frontmatter in our posts. The above snippet references the custom frontmatter fields `topics` and `tags`, which are taxonomies.


---

Up next: What are taxonomies?
