# Reports from the refactoring battlefield

*and how to put your domain back into the mighty monolith in the age of microservices*

This talk will take you on a journey into the world of overly complicated and overengineered enterprise software and take you back to a saner and simpler world embracing the monolith first approach. 

I will delve into common 

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