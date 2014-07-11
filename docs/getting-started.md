---
layout: docs
title: Getting started
prev_section: home
next_section: first-steps
permalink: /docs/getting-started/
---

We will begin install

<div class="note">
  <h5>What will we see here?</h5>
  <p>We will install lein and we will launch our first REPL.</p>
</div>

## Installing the REPL

The best way to prepare a working system for clojure is to install
`lein`. You can think of `lein` as a kind of nice `maven` for the
Clojure world. The instructions to install `lein` are in its homepage
at <http://leiningen.org>. We have sum it up for you here:

{% highlight text %}
LEIN_URL='https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein'
LEIN_CMD='/usr/local/bin/lein'
mkdir -p "$(dirname "${LEIN_CMD}")"
curl -sSL -o "${LEIN_CMD}" "${LEIN_URL}"
chmod a+x "${LEIN_CMD}"
{% endhighlight %}

Then to start a REPL type:

{% highlight text %}
lein repl
{% endhighlight %}

If everything worked out well, you should see something like this:

{% highlight text %}
nREPL server started on port 63549 on host 127.0.0.1
REPL-y 0.2.1
Clojure 1.5.1
    Docs: (doc function-name-here)
          (find-doc "part-of-name-here")
  Source: (source function-name-here)
 Javadoc: (javadoc java-object-or-class-here)
    Exit: Control+D or (exit) or (quit)
 Results: Stored in vars *1, *2, *3, an exception in *e

user=>
{% endhighlight %}

That's nothing, though. The real magic happens when you start creating blog
posts, using the front-matter to control templates and layouts, and taking
advantage of all the awesome configuration options Jekyll makes available.

If you're running into problems, ensure you have all the [requirements
installed][Installation].

[Installation]: /docs/installation/
