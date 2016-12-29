---
layout: post
title:  "Gems Missing from Bundle Outdated in 1.13, Part 3"
date:   2016-12-29
---
In [Part 2](/2016/12/13/gems-missing-bundle-outdated-1-13-part-2.html), a large 
flailing had begun trying to get a suitable Specification instance to use 
in the tests. In part 3 below you'll get the fuller explanation as to why, but 
as already mentioned in a prior [Behind The Scenes post](/2016/12/02/behind-the-scenes-02-dec-2016.html),
some of it is due to the fact that all 3 of these parts are actually a recreation
of work that I'd already done before recording these episodes for RealCodez. Well,
not even a true recreation, I really am starting from scratch again, forgetting
some of the specifics from the first time around, and thus fueling some of my 
stubbornness to not just get on with it and use a mock. The rest of the stubbornness 
is just part of my charm.

As a supporting note for one of my preferences against mocks, around 22:05 we
see a usage of a spec inside `Bundler::Index` that not only uses the `name` of
the spec but also its `full_name`. Re-using a supporting production class gets
us this 'for free' in this case (it won't always) ... but passing in a mock
to code like that can be annoying as we discover and have to implement the various 
items required of the test double.

(Also note, I'm a mock classicist, as 
[Fowler describes here](http://martinfowler.com/articles/mocksArentStubs.html#ClassicalAndMockistTesting),
in case you, kind reader, are annoyed at my lazy use of the term 'mock'). 
 
Another note: around the 12:30 mark, I dig into a novel (to me, at least) usage
of the Forwardable module to redirect an `Enumerable` method (`:each`) to another
method of the `SpecSet` class. This gets used when the `detect` method is called
on `SpecSet`, but what I fail to call out for those who may not know, is that the 
`detect` method on `Enumerable` itself calls `each`. And that doesn't even appear 
at all in the stack trace. 
  
To describe another way, `Definition` calls `detect` on the `SpecSet`, and `SpecSet` 
includes `Enumerable`. When `detect` is called, the `Enumerable` module calls
`each`, and then `each` is defined in `SpecSet` to be forwarded to `sorted`. 

Overall, the good news is in this episode I've finally reached a conclusion, and the meta 
lesson here is even writing the same solution twice can be fraught with peril. 

Hope you enjoy the episode. Shoot me an email below 
or hit up @realcodez on twitter or [facebook](https://www.facebook.com/realcodez).

_If you aren't a subscriber, you'll see the trailer below with an option to rent the specific episode._

<iframe src="https://player.vimeo.com/video/197323193" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

<hr width="20%"/>

### Links

- [Bundler PR #5105](https://github.com/bundler/bundler/pull/5105) ([original issue #4979](https://github.com/bundler/bundler/issues/4979))
- [PoLS](https://en.wikipedia.org/wiki/Principle_of_least_astonishment)
- [Stubbornness](http://4.bp.blogspot.com/-hHoMCtD3QWE/VmYCp6FJnuI/AAAAAAAADrc/y1W2KghFzKE/s1600/Pouting%2Bgirl.jpg)
