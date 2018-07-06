---
title: "Define Homepage"
date: 2018-07-05T00:19:04+10:00
draft: false
---

> The homepage template is the only required template for building a site and therefore useful when bootstrapping a new site and template. It is also the only required template if you are developing a single-page website.

> -- [Hugo Docs](https://gohugo.io/templates/homepage/)

Let's create a `_index.md` file under `content` and use the example homepage template from the docs. 

```
hugo new _index.md
```

```md
---
title: "Index"
date: 2018-07-04T14:27:03+10:00
draft: true
---
```

Let's change a few things. 
```
---
title: "My Awesome Homepage"
date: 2018-07-04T14:27:03+10:00
draft: false
subtitle: "made by myself"
---

A longer blurb Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do 
eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim 
veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo 
consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse 
cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non 
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

```
Let's break down the example template in the docs, ignoring for the moment the references to "base templates":

```html 
<!-- layouts/index.html body -->
  <header class="homepage-header">
    <h1>{{.Title}}</h1>
    {{ with .Params.subtitle }}
    <span class="subtitle">{{.}}</span>
    {{ end }}
  </header>
  <div class="homepage-content">
    {{.Content}}
  </div>

```

{{% img rsc="images/005-homepage.png" alt="Screenshot" %}}

You can easily see here the relationships between the contents of the `content/_index.md` file, the variables used in `layouts/index.html` and what it looks like when rendered.

Change the text around and see it reflected immediately!

What's with that `with`, you ask?

```html 
{{ with .Params.subtitle }}
<span class="subtitle">{{.}}</span>
{{ end }}
```
The [docs](https://gohugo.io/functions/with/) say this about `with`: 

>An alternative way of writing an if statement and then referencing the same value is to use with instead. with rebinds the context (.) within its scope and skips the block if the variable is absent or unset.

So: 
```html
{{ if x }}
  {{ x }}
{{ end }}
```
```html 
{{ if isset .Params "subtitle" }}
<span class="subtitle">{{.Params.subtitle}}</span>
{{ end }}
```

is the same as 
```html 
{{ with x }}
  {{ . }}
{{ end }}
```
```html
{{ with .Params.subtitle }}
<span class="subtitle">{{.}}</span>
{{ end }}
```

{{% img rsc="images/005-with.png" alt="Screenshot" %}}


It may not seem like much right now, but it makes things really convenient later on! 

---
The next chunk of code on the example homepage prints out the summaries of the first 10 pages. Let's put a red border around it so we see where it is:

```html 
<div style="border:1px solid red">
  {{ range first 10 .Data.Pages }}
      {{ .Render "summary" }}
  {{ end }}
</div>
```

Let's break this down.

### `range`
> Iterates over a map, array, or slice.

> -- [Hugo Docs](https://gohugo.io/functions/range/)

### `.Render`

> The view is an alternative layout and should be a file name that points to a template in one of the locations specified in the documentation for Content Views.

> -- [Hugo Docs](https://gohugo.io/functions/render/#readout)

This means that to use `{{ .Render "summary" }}` we need to have a file `layouts/_default/summary.html`.

Let's put a blue border around it so we know where it is:

```html 
<!-- layouts/default/summary.html -->
<div style="border:1px solid blue; margin:2px">
  {{ .Content }}
</div>
```

This is useful if the same view is used in different places. We don't have to define its own view though and could simply do

```html
<div style="border:1px solid red">
  {{ range first 10 .Data.Pages }}
    <div style="border:1px solid blue; margin:2px">
      {{ .Content }}
    </div>
  {{ end }}
</div>
```

{{% img rsc="images/005-range-pages.png" alt="Screenshot" %}}

But wait, why is it empty??

Let's go back to our posts, shall we: 

```
---
title: "001"
date: 2018-07-04T10:58:31+10:00
draft: true
---

## This is just some lorem 

...

```
There it is, we forgot to set `draft` to `false`!

If the posts are not ready for publishing yet, but you want to preview while using `hugo server` you could also use the `--buildDrafts` flag:

```
hugo server --buildDrafts
```

{{% img rsc="images/005-summary.png" alt="Screenshot" %}}

---

But what if we don't want the contents of the posts on the homepage? 

No problem!

The [Hugo Docs](https://gohugo.io/variables/page/) have a list of page variables we can access. For example, we could instead show:

```html 
<!-- layouts/_default/summary.html -->
<div style="border:1px solid blue; margin:2px">
  <h4><{{ .Title }}</h4>
  <h6>{{ .WordCount }} words written on {{ .Date }}</h6>
  
  {{ .Summary }}
</div>
```

{{% img rsc="images/005-summary2.png" alt="Screenshot" %}}

Awesome!

How do we see individual posts now, you ask?

---

Up next: We define a single page template