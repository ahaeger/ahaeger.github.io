---
layout: post
author: haeger
tags: cli click cookie-cutter
---

When working on the `es` CLI tool I wrote about earlier, it strook me that a lot of the things I created was probably 
pretty generic but more fully featured functionality for a CLI. So I made a cookie cutter out of it!

# Stuff every CLI needs

Here are some things I added to this cookie cutter that I think most CLIs benefit from:

- Logging setup
    - Log level flags
    - Log directory
- Something else
- And some more

Here's the code for the thingy-thingy:

{% highlight python %}
# factorial.py

def factorial(i: int):
  if i == 0:
    return 1
  else:
    return i * factorial(i-1)  # This is the fancy part.

if __name__ == '__main__':
  n = 5
  n_factorial = factorial(n)
  print(n_factorial)
{% endhighlight %}
