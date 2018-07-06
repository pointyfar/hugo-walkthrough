---
title: "Taxonomies"
date: 2018-07-05T00:55:31+10:00
draft: false
---

[Details@Docs](https://gohugo.io/content-management/taxonomies/): What are taxonomies?

> Taxonomies are classifications of logical relationships between content.

> -- [Hugo Docs](https://gohugo.io/content-management/taxonomies/#what-is-a-taxonomy)

Hugo has `tags` and `categories` configured by default. Let us [configure Hugo](https://gohugo.io/content-management/taxonomies/#configuring-taxonomies) to recognise `topics` as well.

```toml
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site That I Built Myself"
theme = "walkthrough"

[taxonomies]
  topic = "topics"
  tag = "tags"
```

---

Let's put tags and topics in some of our posts.

```md
---
title: "My First Post"
date: 2018-07-04T14:03:01+10:00
draft: false
topics:
  - lorem
---
```

```md
---
title: "My Second Post"
date: 2018-07-04T14:08:01+10:00
draft: false
topics: 
  - lorem 
  - ipsum
  - lorem ipsum
tags:
  - red
  - yellow
---
```

```md
---
title: "My Third Post"
date: 2018-07-04T14:08:07+10:00
draft: false
tags: 
  - red
---

```

{{% img rsc="images/007-single-page-topics-tags.png" alt="Screenshot" %}}


Read up [here](https://gohugo.io/content-management/front-matter/) to find out more about frontmatter.

---

Up next: We define a list page template.