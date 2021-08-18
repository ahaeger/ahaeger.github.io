---
layout: post
title: Introducing esok - the Elasticsearch CLI
tags: elasticsearch cli ops
published: 2021-08-18 21:16:00 +0200
image: /assets/images/esok.gif
image-credit: 
image-credit-link: 
image-title: It was way harder than expected to piece this gif together.
---

My team at Spotify maintain the Elasticsearch clusters that back Spotify's
search feature. These are big deployments of Elasticsearch across several
regions, with multiple clusters in each region. This of course entails a bunch
of ops work, so I started to collect some common operations. Eventually it
resulted in me working on this CLI on my hack time. What I wanted was to 1) run
the same command on each corresponding deployment in all the regions/sites, 2)
group common chains of curls into a single command and finally 3) make something
slightly more human-friendly than curls in the bash history. The result
is [`esok`][Github]!

This tool is still missing lots of the API endpoints that Elasticsearch has,
I've mainly been dogfooding it myself with stuff I've felt a need for (and had
time to implement) and that's probably how I'll keep on going. I haven't really
had any intentions for 100% coverage of the Elasticsearch API, just the stuff
that is actually needed from an "operations perspective".

I've been trying to strike some balance between strictly mirroring the API and
enriching with my own "custom" commands. An example of custom command
is `esok index shards <INDEX> <COUNT>`, which allows you to specify how many
shards you want per node of that particular index (and you don't have to think
about cluster size or primary shard count). There's also some handy commands for
reading (`esok index read`) and writing json (`esok index write`) to an index.
I'm not sure if this will end up being confusing, time will have to tell.

As for the name; `es` was already taken, so I asked my colleagues for ideas and
`esok` made the most sense. I switch between reading/pronouncing it as "e-sock"
or "ES, ok?". Whatever floats your boat!

`esok` is fully open source, find it on [Github] and [PyPI] along with
instructions on how to install it. Many thanks to Hynek Schlawack, for
his [guide on Python packaging][Hynek], and my colleagues at Spotify, who's been
my early test users.

## Example commands

Create an index from a mapping, write some data to it and atomically swap 
an alias to the new index, in all sites of the "catalog" cluster.

```bash
esok --cluster catalog index create product-2021-05-21 ./product-mapping.json
esok --cluster catalog index write --index-name product-2021-05-21 ./data.json
esok --cluster catalog alias swap products product-2021-05-20 product-2021-05-21
```

Various utilities:

```bash
esok index list  # List indices
esok index shards products-2021-05-2 2  # Set replicas so that there's two shards on each host
esok index read products-2021-05-20 > dump.json  # Dump documents to file 
esok alias list  # List alises
```

I hope you find this tool useful!

[Github]: https://github.com/ahaeger/esok
[PyPI]: https://pypi.org/project/esok/
[Hynek]: https://hynek.me/articles/sharing-your-labor-of-love-pypi-quick-and-dirty/
