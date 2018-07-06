---
title: "Adding Images"
date: 2018-07-05T13:59:09+10:00
draft: false
---

We've just seen how easy it is to add a photo to our templates. What about to content?

Let's write a new post `hugo new post/this-has-images.md`

We can use the [markdown syntax](https://www.markdowntutorial.com/lesson/4/) for adding images to posts.

We can also use Hugo's builtin [figure shortcode](https://gohugo.io/content-management/shortcodes/#figure) (Read more about shortcodes [here](https://gohugo.io/content-management/shortcodes/))

---

Using our logo image located in `static`

```bash
...
├── static
│   └── my-logo-placeholder-fit.png
...
```

```md
---
title: "This Has Images"
draft: false
---

These use the markdown syntax:

![350x150](http://via.placeholder.com/350x150)
![My Logo](/my-logo-placeholder-fit.png)

---

These use Hugo's builtin shortcode:

{{</* figure src="http://via.placeholder.com/350x150" title="Builtin Shortcode" */>}}

{{</* figure src="/my-logo-placeholder-fit.png" title="My Logo" */>}}

---
```
.*

{{% img rsc="images/013-images.png" alt="Images" %}}

---

Up next: We make a page bundle with resources.
