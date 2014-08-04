---
layout: docs
title: Functions 
prev_section: naming-things
next_section: higher-order-functions
permalink: /docs/functions/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>How to define functions</p>
</div>

Some syntax (stay reassured, not much!) first. To declare a function, the syntax (well we don't reveal all details up front) is:

{% highlight clojure %}
(defn name 
	"documentation [optional]" 
	[arguments] 
		body of the function)
{% endhighlight %}

One trivial example
{% highlight clojure %}
(defn plus-one
	"Adds one to the given number"
  	[n] (+ 1 n))
;; #'user/plus-one
(plus-one 10)
;; 11
{% endhighlight %}

Back to our previous (rather complex) problem, we could write that function as follows:
{% highlight clojure %}
(defn weight [mass]
	(* 9.81 mass))
;; #'user/weight
(weight 70)
;; 686.7
(weight 85)
;; 833.85
{% endhighlight %}	

Nice, but let's imagine you want to provide an alternate version of the `weight` function that accepts the value of the gravity.
The `[arguments] body` can be repeated with different arities like this (note that each block now needs to be wrapped by parentheses):
{% highlight clojure %}
(defn name 
	"documentation [optional]" 
	([arg] 
		body of the function with one argument))
	([arg1 arg2] 
		body of the function with two arguments)))	
{% endhighlight %}

And our `weight` function becomes:
{% highlight clojure %}
(defn weight
  ([mass] (* 9.81 mass))
  ([mass gravity] (* gravity mass)))
;; #'user/weight
(weight 85)
;; 833.85
(weight 85 3.711)
;; 315.435
{% endhighlight %}

Hum, not that bad, however there is a sort of repetition in our code. Why not reuse the general formula for the specific case (with the default gravity)?
That leads us to:
{% highlight clojure %}
(defn weight
	([mass] (weight mass 9.81))
	([mass gravity] (* gravity mass)))
;; #'user/weight
{% endhighlight %}

<div class="note">
  <h5>What have we seen here?</h5>
  <p>One syntax to define a function (we'll see alternatives later on).</p>  
</div>


