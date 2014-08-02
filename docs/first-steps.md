---
layout: docs
title: First steps
prev_section: getting-started
next_section: calling-a-function
permalink: /docs/first-steps/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>We will play with the clojure syntax within the REPL.</p>
</div>

## Note about examples

From now on, you'll be playing inside the REPL.
If not done yet, please refer to 
[getting-started](/docs/getting-started/)
to install and launch a REPL.

The code snippets will be presented like this:

{% highlight clojure %}
"hello clojure"
;; => "hello clojure"
{% endhighlight %}

so that they can easily be cut and pasted in your REPL, where they will be displayed as

{% highlight text %}
user=> "hello clojure"
"hello clojure"
{% endhighlight %}



Because `;;` are comments in Clojure.

## Let's see what Clojure understands

{% highlight clojure %}
;; Numbers?
1
;; => 1
1.0
;; => 1.0
1 2 3
;; => 1
;; => 2
;; => 3
;; Strings?
"hello clojure"
;; => "hello clojure"
{% endhighlight %}

So, that's nice. Clojure seems to understand some expected basics like
numbers and strings. What about lists of things?

{% highlight clojure %}
;; Lists of things are with square brackets
[1 2 3]
;; => [1 2 3]
;; Things in lists can be of mixed types
[1 2.0 "3.1415" "love"]
;; => [1 2 3]
;; Why not parentheses?
(1 2 3)
;; => ClassCastException java.lang.Long cannot be cast to clojure.lang.IFn
{% endhighlight %}

Ah, parentheses seem to be used for something specific. We'll see it
in some seconds.

{% highlight clojure %}
;; Names?
something
;; => CompilerException java.lang.RuntimeException: Unable to resolve symbol: something in this context
{% endhighlight %}

With named things we are not there yet...

<div class="note">
  <h5>What have we seen here?</h5>
  <p>Basic types understood by Clojure.</p>
  <p>Lists of things within square brackets.</p>
</div>