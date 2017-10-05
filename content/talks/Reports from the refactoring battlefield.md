# Reports from the refactoring battlefield

*and how to put your domain back into the mighty monolith in the age of microservices*

This talk will take you on a journey into the world of overly complicated and over engineered enterprise software and take you back to a saner and simpler world embracing the monolith first approach.

In this talk you will learn why it is worth considering refactoring your large overly complicated (enterprise) system rather that starting out from scratch. You will be guided though the process of carving out your actual domain and learn why it is almost always better to design a solid monolith before even considering microservices. You will also learn why practices like testing, logging and proper naming are so very important.




During the takl you will be introduces the common indicators that you are infact 

Overly abstracted layers that hides all useful informauin of porpuse

Having the courage to change large parts of a legacy system


A journey into (regular/overengineered) enterprise design patterns and how to get back to a saner/simpler monlith.


Problems worth pondering

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