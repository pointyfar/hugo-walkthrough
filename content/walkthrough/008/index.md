---
title: "Define List Page"
date: 2018-07-05T00:57:42+10:00
draft: false
---


Let's go back to this snippet on the homepage. 

```html
  {{ range first 10 .Data.Pages }}
      {{ .Render "summary"}}
  {{ end }}
```

So far we only have three posts, so iterating over the `first 10` captures all three. But what if we have 20? 200? Wouldn't it be nice if there was a page that listed all our content?

[Details@Docs](https://gohugo.io/templates/lists/)

Let's open up `layouts/_default/list.html` and put some code in:

```html 
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>{{.Site.Title}}</title>
  </head>
  <body>
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
  </body>
</html>
```

{{% img rsc="images/008-list-page-post.png" alt="Screenshot" %}}

Easy Peasy.

You may have noticed by now that some lines of HTML code across `index.html`, `single.html` and `list.html` are the same. Wouldn't it be nice if we could write those lines once and reuse them where we need them?

We can in fact do exactly that!