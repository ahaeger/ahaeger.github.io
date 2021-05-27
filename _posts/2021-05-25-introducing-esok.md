---
layout: post
title: Introducing esok - the Elasticsearch CLI
tags: elasticsearch cli ops
published: 2021-05-25 19:53:00 +0200
image: 
image-credit: 
image-credit-link: 
image-title: 
---

My team at Spotify maintain the Elasticsearch clusters that back Spotify's
search feature. These are big deployments of Elasticsearch across several
regions, with multiple clusters in each region. This of course entails a bunch
of ops work, so I started to collect some common operations. Eventually it
resulted in me working on this CLI on my hack time, because what I wanted was to
1) run the same command on each corresponding deployment in all the regions, 2)
group several requests into a single command and finally 3) make something
slightly more human-friendly than curls in the bash history. The result
is `esok`!

This tool is still missing lots of the API endpoints that Elasticsearch has, but
my intention hasn't been to have 100% coverage (PRs welcome though!) - I've
mainly been dogfooding it myself with stuff I've felt a need for. I've been
trying to strike some balance between mirroring the API and simplifying some
commands. Not sure where I am on this train of thought...

- Been trying to strike a balance between keeping to the existing API and enriching
  with handy commands where you'd expect them
- Still early days, many things not implemented
- My first PyPI package. Thanks to...
