---
title: "Check-in"
date: 2018-07-05T10:30:29+10:00
draft: false
---

Congratulations! You now got yourself a (very minimal and bare) Hugo site!

A recap of what we've done:

1. [Created a new Hugo site](/walk/001/)
1. [Created a new Hugo theme](/walk/002/)
1. [Wrote index.html](/walk/003/)
1. [Wrote some content](/walk/004/)
1. [Defined homepage template](/walk/005/)
1. [Defined a single page template](/walk/006/)
1. [Defined a custom taxonomy](/walk/007/)
1. [Defined a list page](/walk/008/)
1. [Defined a `baseof` template](/walk/009/)
1. [Defined partials](/walk/010/)

And this is how things look:

{{% img rsc="images/011-homepage.png" alt="Homepage" %}}

{{% img rsc="images/011-single-page.png" alt="Single Page" %}}

{{% img rsc="images/011-list-page.png" alt="List Page" %}}

Not too bad, but there's still a lot more to Hugo!

layouts_01 captures the state of the layouts at this point.

```
...
└── themes
    └── walkthrough
        ├── archetypes
        │...
        ├── layouts
        │...
        ├── layouts_01                <-- HERE
        │   ├── 404.html
        │   ├── _default
        │   │   ├── baseof.html
        │   │   ├── list.html
        │   │   ├── single.html
        │   │   └── summary.html
        │   ├── index.html
        │   └── partials
        │       ├── footer.html
        │       └── header.html
        ├── LICENSE
        ├── static
        │...
        └── theme.toml
```