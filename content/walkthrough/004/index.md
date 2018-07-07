---
title: "Write Content"
date: 2018-07-05T00:15:27+10:00
draft: false
---

Time to write some content! 

[Details@Docs](https://gohugo.io/content-management/organization/): Content organisation in Hugo

```
hugo new post/my-first-post.md
```
Running the above command adds a `my-first-post.md` file under `content/post`: 
```sh
├── archetypes
│   └── default.md
├── config.toml
├── content
│   └── post
│       └── my-first-post.md
├── data
├── layouts
├── README.md
├── static
└── themes
```
  
  
`my-first-post.md`

```md
---
title: "My First Post"
date: 2018-07-04T14:03:01+10:00
draft: true
---
```

Let's write a couple more posts

```
hugo new post/my-second-post.md
hugo new post/my-third-post.md
```

and put some lorem in there.

```md
---
title: "My First Post"
date: 2018-07-04T14:03:01+10:00
draft: true
---

Quid ingeniis mandaremus, sint constias id exercitation. Culpa tractavissent 
mandaremus anim mandaremus non hic sint pariatur ab cupidatat relinqueret o 
iudicem in anim ubi ne culpa eiusmod est amet cupidatat ab praesentibus, veniam 
cernantur est aliquip, nam ex velit quamquam a summis quibusdam laborum. Non 
nisi fidelissimae ne illum mandaremus a litteris, veniam eiusmod de eiusmod e 
singulis ubi ingeniis. Nostrud eu labore nescius et officia non probant, te 
deserunt relinqueret eu constias dolor magna aut dolor, se aute appellat in 
incididunt fidelissimae sed excepteur, si elit deserunt tractavissent, culpa 
familiaritatem proident ipsum fabulas.Fugiat nam proident hic irure. 

```

```md
---
title: "My Second Post"
date: 2018-07-04T14:08:01+10:00
draft: true
---

Commodo quid fugiat deserunt quorum iis arbitror amet et possumus coniunctione. 
Veniam possumus aut cohaerescant. Ea hic reprehenderit, export officia 
exquisitaque. Arbitror sint illum admodum illum est tempor senserit ingeniis id 
laboris voluptatibus non nostrud, culpa ingeniis iudicem o ubi te legam anim 
quid, fore officia ea minim malis et malis qui sed dolore pariatur ea e fore 
quid culpa doctrina.Malis si doctrina do aliqua, aute adipisicing incididunt 
fore constias. Eu veniam veniam te nescius a minim o in fore deserunt, aliquip 
et fore mandaremus, de laboris an mentitum e voluptate anim occaecat expetendis, 
quibusdam noster constias, incididunt iis duis iis nostrud de proident. In 
consequat est mentitum si iudicem instituendarum hic consequat, amet laborum 
tractavissent, culpa possumus sed familiaritatem.

```

```md
---
title: "My Third Post"
date: 2018-07-04T14:08:07+10:00
draft: true
---

Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor 
incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis 
nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. 
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu 
fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in 
culpa qui officia deserunt mollit anim id est laborum.

```

---

Up next: We make the homepage more interesting!