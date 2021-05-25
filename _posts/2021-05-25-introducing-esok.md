---
layout: post
title: Introducing esok - the Elasticsearch CLI
tags: elasticsearch es cli ops
published: 2021-05-25 19:53:00 +0200
image: 
image-credit: 
image-credit-link: 
image-title: 
---

- ES at Spotify
- Ideally we automate away manual tasks, but find myself doing a bunch of curls anyway
- Deployed in several regions led to multiple clusters
- The API makes sense, but messy bash history and some things could just be more human

- esok was made to 
  - apply the same command to several deployments across regions
  - simplify some on-call common operations

- Been trying to strike a balance between keeping to the existing API and enriching
  with handy commands where you'd expect them
- Still early days, many things not implemented
- My first PyPI package. Thanks to...
