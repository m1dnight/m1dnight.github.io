---
layout: post
title:  "We tested 7 languages for realsies"
date:   2025-07-14 11:59:25 +0200
categories: elixir performance java js python rust
draft: true
---

A while ago, I saw this blog article[ref] going round that would make my professor of
'Methods of Scientific Research' explode with anger and flunk the internet. The
article was by no means proper science. It was not reproducible, it did not show
its sources, it did not show the benchmarks it ran, and it did not show numbers,
but rather "this thing broke, this didnt". This is my attempt to try and do
better.

I tried to write a simple webserver in as many languages as I could
semi-confidently do, and measured how they held up under pressure.

I rented a bigass server and setup a k6 cluster to badger the things
until they cried for mommy.

### What culd go wrong

I am not going to pretend I wrote the most best fastest webserver in each
language. I picked the popular framework du jour for each language, and went
through their documentation to implement a basic example.

The most challenging one turned out to be Rust. Using just the Tokio library I
got only 800 req/s[ref]. Switching over to Axum made it as fast as the other ones, so
I think that's good. If you can improve on this, or spot obvious mistakes, do
let me know in a PR. When I have the time (and money) I will setup a CI that
runs each benchmark for a new PR.

 - Something about request pipelining here

### Iteration 1

The first iteration was a bunch of webservers that do nothing more than return `{"response": "ok"}`.
A few rules.

 - To keep things fair, the response is an actual data structure that is turned into JSON using the frameworks in the language.
 - Each HTTP request/response is compared so that the actual output is the same, and the same amount of bytes are being shuffled per request.
   This is verified using `curl -vv`. Examples of each request can be found under `k6/iteration_n/`


### Nerves

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight elixir %}
def Foo do
end
{% endhighlight %}


# https://sciencenotes.org/scientific-method-vocabulary-terms/