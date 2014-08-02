---
layout: docs
title: Naming things
prev_section: calling-a-function
next_section: lazyness
permalink: /docs/naming-things/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>The equivalent to declaring a variable in other languages.</p>
  <p>In Clojure: how to bind a value to a name and use it again later.</p>
</div>

## Symbols

We have seen in the [previous section](/docs/first-steps#lets-see-what-clojure-understands) following error in the REPL:

{% highlight clojure %}
;; Names?
something
;; => CompilerException java.lang.RuntimeException: Unable to resolve symbol: something in this context
{% endhighlight %}

From the error message, we can learn that a naked name like
`something` is called a `symbol` in Clojure. And in this case, Clojure
is not able to _resolve_ it, meaning there doesn't seem to be
something attached to this `symbol`. So, how do we attach a value to a
`symbol`?

## def

Attaching a value to a `symbol` is usually refered to as `binding` in
Clojure.

<div class="note unreleased">
  <h5>Binding a symbol to a value</h5>
  <p>In Clojure the syntax to bind a value to a symbol is: `(def` followed by the symbol followed by the value and a closing `)`.</p>
</div>

Ok, so let's use it.

{% highlight clojure %}
something
;; => CompilerException java.lang.RuntimeException: Unable to resolve symbol: something in this context
(def something "a string")
;; => #'user/something
something
;; => "a string"
{% endhighlight %}

After defining the symbol `something` (i.e. binding the `symbol`
`something` to the value `"a string"`) Clojure doesn't complain
anymore.

As you might expect, you can use defined symbols as arguments of a
function call:

{% highlight clojure %}
(def apples 10)
;; => #'user/apples
(def blackberries 6)
;; => #'user/blackberries
(+ apples blackberries)
;; => 16
{% endhighlight %}

Yes, in Clojure you can add apples and blackberries. And you can also
bind the result of a function to another `symbol`.

{% highlight clojure %}
(def g 9.81)
;; => #'user/g
(def mass 70.0)
;; => #'user/mass
(def weight (* g mass))
;; => #'user/weight
weight
;; => 686.7
{% endhighlight %}

This example whets our apetite to create a function that let's us
calculate the weight of any mass, doesn't it?

<div class="note">
  <h5>What have we seen here?</h5>
  <p>Syntax to define a symbol.</p>
  <p>Binding a symbol to a value.</p>
  <p>Binding a symbol to the result of a function call.</p>
</div>