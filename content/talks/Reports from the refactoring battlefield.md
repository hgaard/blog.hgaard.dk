+++
author = "Jakob Højgaard"
categories = ["refactoring", "TDD", "DDD"]
date = 0001-01-01T00:00:00Z
description = ""
draft = true
slug = "refactoring-a-large-running-system"
tags = ["refactoring", "TDD", "DDD"]
title = "Experience gained from refactoring a large legacy system"

+++

# Avoid the microservice fallacy: put your domain back into the mighty monolith

This talk will take you on a journey into the world of overly complicated and over engineered enterprise software and take you back to a saner and simpler world embracing the monolith first approach.

In this talk you will learn why it is worth considering refactoring your large overly complicated (enterprise) system rather that starting out from scratch. You will be guided though the process of carving out your actual domain and learn why it is almost always better to design a solid monolith before even considering microservices. You will also learn why practices like testing, logging and proper naming are so very important.

## Bio

Software developers swiss-army knife, farther of tree, brewer, rookie surfer, Consultant at Readify


## Problems worth pondering

* overly abstract (no meaning) naming
  * vendorFactoryServiceInterface!!
* what to focus on when writing tests
* Use the right tools (git, CI, etc...)
* Test test test
* Logging logging logging!

## Notes

* Make sure you undertand why the refactoring is necessary
  * Many valid reasons but be 100% sure you know and understand
* Find a way to break the system into testable "components"
* A lot of tests might be temporay trancient
  * Don't keep from writing tests just because you are not sure they are long lasting
* Software as a crime scene

## Resources

* https://www.infoq.com/presentations/soa-without-esb
* https://www.youtube.com/watch?v=MjIfWe6bn40&feature=youtu.be&t=9m47s
* https://www.amazon.com/Working-Effectively-Legacy-Robert-Martin-ebook/dp/B005OYHF0A/ref=mt_kindle?_encoding=UTF8&me=&dpID=518yKmNefUL&preST=_SY445_QL70_&dpSrc=detail
* https://www.google.com.au/search?q=refactoring+martin+fowler&oq=refactoring+mar&aqs=chrome.0.0l2j69i57j0l3.4935j0j7&sourceid=chrome&ie=UTF-8
* https://m.signalvnoise.com/the-majestic-monolith-29166d022228
