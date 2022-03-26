


## Unit Testing and Documentation

- n C#, you can think of a unit as a method.  You thus write a unit test by writing something that tests a method.  Oh, and it tests something specific about that method in isolation.  Don’t create something called TestAllTheThings and then proceed to call every method in a namespace.
- Unit tests also don’t count as other sorts of tests.  If you create some sort of test that throws thousands of requests for a service you’ve written, that qualifies as a smoke test and not a unit test.  Unit tests don’t generate random data and pepper your application with it in unpredictable sequences.  They’re not something that QA generally executes.

- unit tests don’t exercise multiple components of your system and how they act.  If you have a console application and you pipe input to it from the command line and test for output, you’re executing an end-to-end system test — not a unit test.




## Art of README
### This project makes it easy to:
- Bootstrap your open source project properly
- Make sure everyone gets what you're trying to achieve with your project

***No README means developers will need to delve into your code in order to understand it.***