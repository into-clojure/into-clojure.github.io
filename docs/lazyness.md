---
layout: docs
title: Lazyness
prev_section: naming-things
next_section: home
permalink: /docs/lazyness/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>Lazyness is a powerful concept in Clojure that will allow us to go "To infinity, and beyond!"</p>
</div>

<div class="note info">
  <h5>What is lazyness actually?</h5>
  <p>Lazyness means delaying the evaluation of something until it is actually needed. </p>
</div>

A classical example, in Java, is the && operator.
{% highlight java %}
if (anObject != null && anObject.isSomething()) {
	// do something with anObject ...
}
{% endhighlight %}

In that case, if anObject is null the second part of `&&` is not evaluated. 
The expression `anObject.isSomething()` is evaluated only when needed: lazyness at work. 

We'll expand on this notion with a challenge: build the list of *all* even numbers. Although that list is infinite, there is a way to manipulate such a concept.

Let's start small with a function that returns the next even number after a given one:

{% highlight clojure %}
(defn next-even [n]
  (+ 2 n))
;;#'user/next-even
(next-even 0)
;; 2
(next-even 2)
;; 4
{% endhighlight %}

So far, so good, what would look like our all-even function?

To make you feel the solution, let's manually build the list of the first even numbers:
{% highlight clojure %}
(cons 0 [])
;; (0)
(cons 0 (cons (next-even 0) []))
;; (0 2)
(cons 0 (cons (next-even 0) (cons (next-even (next-even 0)) [])))
;; (0 2 4)
{% endhighlight %}

It looks like our algorithm will be to `cons` the current element to the list of the next even numbers.

Let's try a first version
{% highlight clojure %}
(defn all-even-1
  ([]  (all-even-1 0))
  ([n] (cons n (all-even-1 (next-even n)))))
;; #'user/all-even-1
user=> (take 10 (all-even-1))
;; StackOverflowError   clojure.lang.Numbers$LongOps.add (Numbers.java:430)
{% endhighlight %}

<div class="note">
  <h5>What have we seen here?</h5>
</div>