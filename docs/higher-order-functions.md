---
layout: docs
title: Higher order functions 
prev_section: functions
next_section: home
permalink: /docs/higher-order-functions/
---

<div class="note">
  <h5>What will we see here?</h5>
  <p>How functions are first-class citizens.</p>
</div>

From [wikipedia](http://en.wikipedia.org/wiki/Higher-order_function):

<div class="note info">
a <b>higher-order function</b> ... is a function that does at least one of the following:
<br />
<i>takes one or more functions as an input</i>
<br />
<i>outputs a function</i>
</div>

Alright, you remember the `weight` function that computed the `weight` for a given `mass` and optionnaly a `gravity`?

Let's generalize, and build a function that will build other functions taking this time the value of gavity.
Just before that, we must explain one minor shortcut we took in our previous chapter.

{% highlight clojure %}
(defn name 	
  [arg] 
    body of the function)
;; is equivalent to
(def name 	 
  (fn [arg] 
	body of the function))
{% endhighlight %}

So, the `plus-one` function can also be written as
{% highlight clojure %}
(def plus-one
  (fn [n] (+ 1 n)))
;; #'user/plus-one
(plus-one 1)
;; 2
((fn [n] (+ 1 n)) 3)
;; the same function (but anonymous this time) is applied to 3
{% endhighlight %}

Armed with this new knowledge, you guess that our builder function will look like:
{% highlight clojure %}
(defn build-weight [gravity]
  (fn [mass] ...))
{% endhighlight %}  

<div class="note unreleased">
  <h5>Mind the gap</h5>
  <p>Please realize that our build-gravity function is a function that returns another function.</p>
  Amazing, no?
</div>

{% highlight clojure %}
(defn build-weight [gravity]
  (fn [mass] (* gravity mass)))
;; #'user/build-weight
(def earth-weight (build-weight 9.81))
;; #'user/earth-weight
(def mars-weight (build-weight 3.711))
;; #'user/mars-weight
(earth-weight 70)
;; 686.7
(mars-weight 70)
;; 259.77
{% endhighlight %} 

