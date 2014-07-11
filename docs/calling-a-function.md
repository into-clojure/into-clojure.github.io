---
layout: docs
title: Calling a function
prev_section: first-steps
next_section: naming-things
permalink: /docs/calling-a-function/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>How to call a function and overcome the parentheses fear.</p>
</div>

## Let's try to sum 1 and 1

{% highlight clojure %}
1+1
;; => NumberFormatException Invalid number: 1+1  clojure.lang.LispReader.readNumber
{% endhighlight %}

Mh... that doesn't seem to work. Maybe we need some spaces?

{% highlight clojure %}
1 + 1
;; => 1
;; => #<core$_PLUS_ clojure.core$_PLUS_@204b7b1>
;; => 1
{% endhighlight %}

That doesn't make Clojure complain, but doesn't yield us to the
expected result though.

<div class="note info">
  <h5>Mind the gap!</h5>
  <p>In the next section you will learn 90% of the Clojure syntax.</p>
</div>

## Calling a function

<div class="note unreleased">
  <h5>Function call</h5>
  <p>In Clojure the syntax to call a function is: `(` followed by the
function followed by the arguments and a closing `)`.</p>
</div>

This is so important that we want to say it again: In Clojure the
syntax to call a function is: `(` followed by the function followed by
the arguments and a closing `)`, i.e.:

{% highlight clojure %}
(function arguments)
{% endhighlight %}


So, taking our addition from previous example, we can run in again on
the REPL applying the first rule we just learned:

{% highlight clojure %}
(+ 1 1)
;; => 2
{% endhighlight %}

Oh yeah. That works. And moreover, that works also inside a function
call, i.e. this function calling mechanism works well in a nested
structure:

{% highlight clojure %}
(+ 1 (+ 1 1))
;; => 3
{% endhighlight %}

And that works deeply enough:

{% highlight clojure %}
(+ 1 (+ 1 (+ 1 (+ 1 (+ 1 (+ 1 1))))))
;; => 7
{% endhighlight %}

Well, this example is a bit silly. Luckily enough, the `+` function
wisely knows how to handle several arguments:

{% highlight clojure %}
(+ 1 1 1 1 1 1 1)
;; => 7
{% endhighlight %}

<div class="note">
  <h5>What have we seen here?</h5>
  <p>Syntax to call a function.</p>
  <p>Nesting of function calls.</p>
  <p>Functions with different number of arguments.</p>
</div>