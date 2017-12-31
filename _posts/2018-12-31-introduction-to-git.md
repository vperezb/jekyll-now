---
layout: post
title: A brief introduction to Git
categories: [tech]
tags: [devops, git]

---

Few must-know commands to start working with Git.

To tell Git who you are:

```git
git config --global user.email "victor.perez.berruezo@gmail.com"
git config --global user.name "vperezb"
```

Clone a repo:

```git
git clone git@path/user/repo
```

To stash all:

```git
git add .
```

To stash specific file:

```git
git add <file>
```

To commit:

```git
git commit -m  "this is the commit message"
```

To push to the server:

```git
git push origin master
```
