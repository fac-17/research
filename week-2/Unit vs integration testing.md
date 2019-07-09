---
title: 'Unit vs integration testing'
disqus: hackmd
---

# To do:
- Brief outline of other tests
- Give clear and concise defn of Unit/Int. testing [Gregor]
---
- Some code snippets of each test (ideally tailored to-do list)
- Unit test example (see above) [Jack and Sarah]
---
- Best practice for both
- Why should we do each? [Leonie]
---
- Table of differences [Gregor]
- Conclusion



Unit vs integration testing
===

> ### What happens when you don't test: 
![...](https://media.giphy.com/media/3o7rbPDRHIHwbmcOBy/giphy.gif)

#### Types of Testing
There are several types of software engineering test such as 
- Unit Testing
- Integration Testing
- Functional Testing / Acceptance Testing: 
    - Functional testing is defined as the testing of complete functionality of some application. You might use a unit test to test an individual function and an integration test to check that two parts of the play nice, functional testing tests the whole.
- System Testing
    - Checking whether the application's parts work together as part of a system - this is applicable when parts are created independent of one another. 

- Usability Testing / UI testing
    - Checking that the application is usable from a UI point of view.

However, I’ll be talking on Unit and Integration testing here.

#### Differents testing frameworks
- SuperTest
- Mocha
- Chai
- Tape
- Jasmin
- Jest

## What is a unit test?

### Definition
**A unit test tests the smallest units of code in isolation.** 

A unit test should essentially just give the function that’s tested some inputs, and then check what the function outputs is correct.

Smallest unit is not defined, but unit test should be as simple as possible. 

Because unit testing requires simple inputs and outputs it encourages us to write code which is simple and concise.

>Everything should be made as simple as possible, but not simpler — Albert Einstein

### Best Practice
Unit Tests have strict rules. Follow the acronym: FIRST

- **Fast**: 
setup & test should run fast (milliseconds) as you may have thousands of tests in your entire project
- **Isolated**
        data used in a test should not depend on the environment in which the test is running. All the data needed for a test should be arranged as part of the test.
- **Repeatable**
        should yield the same results every time and at every location where they run.No dependency on date/time or random functions output.
- **Self-Verifying**
No manual inspection required to check whether the test has passed or failed
- **Timely**
Should cover every use case scenario (including corner/edge/boundary values)
Should Tests for large data sets, large values, exceptions and errors, illegal arguments or bad inputs. 



### Example - Unit Test (Tape)

```
test('sum should return the addition of two numbers', function (t) {
    let actual = sum(1,2);
    let expected = 3;
    t.equal(actual, expected); 
    t.end();
});
```
Test that the sum function is working correctly for 1, 2

### Why and when? 
The **goal of Unit testing** is to test the each unit separately and ensure that each unit is working as expected. It is an **easy and quick way to identify errors**. 

Ideally, unit tests should be performed (by the developer) **all the time** by applying test-driven development. Unit tests need to be an integral part of the development process



# What is an integration test?
### Definition
In integration testing the idea is to test how parts of the system work together – the *integration* of the parts. 

Integration testing is logically an extension of unit testing. When two or more units are combined, they result in what is called an interface. Integration testing identifies problems that occur at the interface between units.

Integration testing helps to ensure that the functional, performance, and reliability between the units that are integrated are working properly.

For example, a unit test for database access code would not talk to a real database, but an integration test would.

### Best Practice
Integratin tests don't have strict rules but general directions to follow: 
- **Repeatable tests**
Test order or dependencies shouldn’t alter the test result. Can be difficult to achieve (for instance when using third-party services)

- **Avoid testing third-party code**
While third-party services may be used in tests, there’s no need to test them. And if you don’t trust them, you probably shouldn’t be using them.


- **Testing relevant actions**
Focus on testing happy scenarios (i.e. no expectional or error conditions)

- **Comprehensible test and assertion**
One quick view of the test should inform the reader what is being tested, how the environment is setup, what is stubbed, when the test is executed, and what is asserted. Assertions should be simple and make use of helpers for better comparison and logging.

- **Easy test setup**
Getting the test to the initial state should be as simple and as understandable as possible.

- **Leave production code free of test code**

- **Relevant logging**
Logging should contain all database queries, API requests and responses, as well as a full comparison of what is being asserted. This can significantly facilitate debugging


### Example - Integration Test (Chai)

Integration test for API GET request. 
```
describe('Todos list API Integration Tests', function() {
  describe('#GET / tasks', function() { 
    it('should get all tasks', function(done) { 
      request(app) .get('/tasks')
        .end(function(err, res) { 
          expect(res.statusCode).to.equal(200); 
          expect(res.body).to.be.an('array'); 
          expect(res.body).to.be.empty; 
          done(); 
        }); 
    });
  });
});
```
When getting all to-do list tasks, we simultaneously test that we:
1. The response has the correct statusCode
2. The response body is an array
3. The response body is empty

### Why and when?


The **goal of the integration test** is to catch bugs at the earlier stage in the software development cycle. Integration testing is mainly useful for situations where unit testing is not enough due to integrations of systems.

- They are used detecting system-level issues.
- Integration testing is easy to integrate with daily builds
- Integration testing is easy to test in local environment

Integration tests **bridge the gap** between unit tests and end-to-end tests:
- Integration tests are often **slower & more complex** than unit tests. Therefore, focus on unit tests unless you absolutely need an integration test. 
- Integration tests **run faster than** end to end tests. Integration testing are more reliable and used in isolating failures.





## When would you use each kind of test?

#### Table comparing the two



| Unit Testing | Integration Testing | 
| -------- | -------- | 
| Unit testing looks at the individual units of code rather than at the interactions between parts of the code.  | Integration testing looks at the interactions between various parts of code|  
| Unit testing has no dependencies outside the code itself| Integration testing can have dependencies on external features such as databases, hardware etc.| 
| Unit testing is a form of White-Box testing | Integration testing is a form of Black-Box testing | 
| Unit testing is intended to identify problems within the code itself| Integration testing is intended to identify problems the code has when interacting with other modules | 
| Unit testing should be the first type of testing undertaking| Integration testing comes after unit testing and before system testing etc.| 

#### Conclusion 
You should have fewer integration tests than unit tests.

![Pyramid of testing](https://cdn.softwaretestinghelp.com/wp-content/qa/uploads/2016/12/image-result-for-unit-testing-vs-functional-testin.png)

---


![](https://i.imgur.com/McoPNZE.png)



(Another table found here:
https://www.guru99.com/unit-test-vs-integration-test.html)


#### Quiz


#### Resources

[FIRTS Principles of Unit Testing](https://github.com/ghsukumar/SFDC_Best_Practices/wiki/F.I.R.S.T-Principles-of-Unit-Testing)

[Integration Test Principles](https://www.toptal.com/nodejs/nodejs-guide-integration-tests)

[Learn Tape](https://github.com/dwyl/learn-tape)

[Integration Test Examples](https://www.codementor.io/olatundegaruba/integration-testing-supertest-mocha-chai-6zbh6sefz)

http://www.softwaretestingclass.com/what-is-difference-between-unit-testing-and-integration-testing/

