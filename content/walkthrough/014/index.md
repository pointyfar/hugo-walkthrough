---
title: "Page Bundles and Resources"
date: 2018-07-05T15:53:44+10:00
draft: false
---

Instead of putting all your assets into `static`, you could keep them together with the content they are related to. 

[Details@Docs](https://gohugo.io/content-management/organization/#page-bundles): What are page bundles?

Let's create a Leaf Bundle

```sh
hugo new post/page-bundle/index.md
```

and put some images in there under `/images`

```
...
├── page-bundle
│   ├── images
│   │   ├── 150.png
│   │   └── 200.png
│   └── index.md
...
```

*images from [https://placeholder.com/](https://placeholder.com/#)*

---

> Page Resources – images, other pages, documents etc. – have page-relative URLs and their own metadata.

> -- [Hugo Docs](https://gohugo.io/content-management/page-resources/)

We can reference the images from the markdown:

```md
![200](./images/200.png)
```

We can also take advantage of Hugo's built in [image processing](https://gohugo.io/content-management/image-processing/) features.

Let's create the shortcode example on that page: 

```html
<!-- layouts/shortcodes/imgproc.html -->
<!-- from https://gohugo.io/content-management/image-processing/ -->
{{ $original := .Page.Resources.GetMatch (printf "*%s*" (.Get 0)) }}
{{ $command := .Get 1 }}
{{ $options := .Get 2 }}
{{ if eq $command "Fit"}}
  {{ .Scratch.Set "image" ($original.Fit $options) }}
{{ else if eq $command "Resize"}}
  {{ .Scratch.Set "image" ($original.Resize $options) }}
{{ else if eq $command "Fill"}}
  {{ .Scratch.Set "image" ($original.Fill $options) }}
{{ else }}
  {{ errorf "Invalid image processing command: Must be one of Fit, Fill or Resize."}}
{{ end }}
{{ $image := .Scratch.Get "image" }}

<figure style="padding: 0.25rem; margin: 2rem 0; background-color: #cccc">
  <img style="max-width: 100%; height: auto;" src="{{ $image.RelPermalink }}" width="{{ $image.Width }}" height="{{ $image.Height }}">
  <figcaption>
    <small>
    {{ with .Inner }}
      {{ . }}
    {{ else }}
      .{{ $command }} "{{ $options }}"
    {{ end }}
    </small>
  </figcaption>
</figure>   
```

and use it in our post:

```md 
---
title: "Page Bundle"
date: 2018-07-05T20:36:45+10:00
draft: false
---

![200](./images/200.png)

{{</* imgproc "images/200.png" Fit "90x90" */>}}
```

{{% img rsc="images/014-image-bundle.png" alt="Images in Page Bundles" %}}
---

Up next: Configuring Hugo