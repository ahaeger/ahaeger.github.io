---
layout: post
author: haeger
title: Introducing "es" - the CLI
tags: elasticsearch es cli ops
---

At Spotify I've been dealing with a bunch of Elasticsearch clusters. Of course, trying 
to do our darndest to stay highly available and all that, we are deployed across several
regions within GCP. This however means that we have identical setups in several places.
The practical implications of having a bunch of Elasticsearch clusters to managed have
meant a bunch of scripting (and of course engineers tend to invent their own).

"es" is CLI utility for wrangling one or several deployments of Elasticsearch.