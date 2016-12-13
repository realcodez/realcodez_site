---
layout: post
title:  "Gems Missing from Bundle Outdated in 1.13, Part 2"
date:   2016-12-13
---
Having set ourselves up to add some smaller scoped tests in 
[Part 1](/2016/11/23/gems-missing-bundle-outdated-1-13-part-1.html) by refactoring the
contributor's bug fix, it's now time to write some tests in Part 2. Scroll to the 
bottom to jump into it.

Before diving in, we address a couple of points of "Olde Business", in particular
a point about referring to something "stupid" I did in Part 1. Learning is not
"stupid" and so I offer up a correction of myself.

That said, later in this episode I refer to a certain step I take as
"feeling stupid" (around the 24:30 minute mark),
and a few minutes later I refer to a similar step as feeling sloppy. I don't really
explain my thinking during the video, so I'd like to expand on it here.

The specific issue is around making a call to a Bundler test helper method called
`build_spec`. The method can receive an optional Array of version strings, and will
return an Array of Gem Specifications, one for each version string passed, which is
very handy. But if only a single version string is passed, the method still returns
the single Gem Specification in an Array. The method being tested only receives a
single spec, and so as I pass the results from `build_spec` along, I repeatedly
forget that fact and move myself along by selecting the `.first` from the result.

Perhaps that method could be renamed to `build_specs` to better express itself,
though that would be a large refactoring throughout the tests, or another option
would be to add a method `build_single_spec` either locally or alongside `build_spec`
among the test helpers.

In any case, again, I wish my language were more precise. I am
identifying a small
[code smell](http://martinfowler.com/bliki/CodeSmell.html) with the naming of the
helper method, but "stupid" and "sloppy" are potentially derogatory for something that
is a normal thing to happen in code.

One last point that I'll discuss more in the next episode has to do with mocks. A large
part of this episode is spent flailing, trying to get a real Specification instance
to do what I need. There's a secondary, behind-the-scenes reason for not using a mock
here, but the larger point is I tend to not favor mocks when I can get a related
class to do its own job. (Of course, I'm saying this and doing this while borrowing 
from a nearby test that I wrote, that has a hand-rolled mock in it). I'll 
offer some more explanation next time, but for now I'll acknowledge that this is an
issue I'm aware of here and I'd love to hear what you think! Shoot an email to the link below 
or hit up @realcodez on twitter.


_If you aren't a subscriber, you'll see the trailer below with an option to rent the specific episode._

<iframe src="https://player.vimeo.com/video/195393394" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

<hr width="20%"/>

### Links

- [Bundler PR #5105](https://github.com/bundler/bundler/pull/5105) ([original issue #4979](https://github.com/bundler/bundler/issues/4979))
- [Code Smell](http://martinfowler.com/bliki/CodeSmell.html)
- [Ruby Memoization Patterns](http://www.justinweiss.com/articles/4-simple-memoization-patterns-in-ruby-and-one-gem/)
- [Red-Green-Refactor](http://www.jamesshore.com/Blog/Red-Green-Refactor.html)
