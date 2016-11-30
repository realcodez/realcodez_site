---
layout: post
title:  "Gems Missing from Bundle Outdated in 1.13, Part 1"
date:   2016-11-23
---
In this, the inaugural episode of RealCodez, we'll be looking at a PR
 submitted by a contributor that fixes a bug in Bundler 1.13 that I
 helped diagnose. The regression causes not all outdated gems to be
 listed in the outdated output. The problem with the PR is the author was, 
 understandably, unable
 to put together a failing test for the bug, so we begin looking at
 how we can refactor the code in question to allow for better testing.

<iframe src="https://player.vimeo.com/video/192851112" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
 
<hr width="20%"/>
 
### Links
 
- [Bundler PR #5105](https://github.com/bundler/bundler/pull/5105) ([original issue #4979](https://github.com/bundler/bundler/issues/4979))
- [Code Envy](http://wiki.c2.com/?FeatureEnvySmell) 
- [Tell, Don't Ask](http://martinfowler.com/bliki/TellDontAsk.html) 
- [Extract Method Refactoring](http://refactoring.com/catalog/extractMethod.html)
- Episode edited by [SamSpielberg](https://www.youtube.com/user/SamSpielberg/videos)

