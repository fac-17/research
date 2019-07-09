
# Test coverage



---


### What is Test Coverage?
**Test coverage** is defined as a metric in Software Testing that measures the amount of testing performed by a set of tests.

It is a technique to ensure that your tests are testing all of your code. :

---

Test coverage _measures the amount of testing performed by a set of test cases_, whenever we can count things and can tell whether or not each of these items has been tested against by a set of given test cases.


![](https://i.imgur.com/7w8XAOX.png)


---


### What Test Coverage does

* Finds **code that isn't accounted for** in test cases 

* Helps to create **additional test cases** to increase coverage

* Identifies **meaningless test cases** that do not increase coverage

---

### Coverage criteria

* **Function coverage**
Is each function in the programme being tested?

* **Statement coverage**
Getting more granular: is each statement being executed by the tests?

* **Condition coverage**
In the case of Boolean expressions: are both outcomes being tested?

---

:information_desk_person:
Depending on the complexity of your project, there can be a number of **additional criteria** such as **edge** coverage, **branch** coverage, etc. 

:scream:
In complex projects, aiming for 100% on all of these criterias may not be a realistic or necessary target.

---

### Illustration :bulb:

```
function example(a, b) {
    if (a == b) {
        return "Testing with (1, 1) will test this"
    }
    if (a > 0) {
        return "Testing with (1, 3) will test this"
        if (a < b) {
            return "Testing with (1, 3) will test this
        } else {
            return "Testing with (1, 0) will test this
        }
    }
    else "Testing with (-1, 3)"
}
```


---

### Why is test coverage useful?

- For the purposes of finding areas not covered by existing test cases

- Determining the existing test coverage helps us to create more test cases for the purposes of increasing test coverage

- It is useful to know how much testing is covered, because it affects the quality of the application


---



- We can identify useless test cases

- Traceability between requirements and test cases

- Impact analysis and change tracking

- Software Testing Life Cycle becomes smoother


---

### What are the drawbacks/limits?

- It measures the coverage of the existing code, but it cannot say anything about what has not been written

- 100% coverage does not mean 100% tested

- Structure-based techniques can miss things

- Aiming for 100% coverage can distract from creating qualitative test that actually test the effectiveness of the code


---

### What are Istanbul and `nyc` :interrobang: 

[Istanbul](https://istanbul.js.org/) - not just the capital of Greece, but so much more! 
Istanbul is a Javascript test coverage tool. It allows you to view how much of your Javascript is covered by the tests you have written. 

* **`nyc`** is the command-line client for Istanbul.  (Which is funny because NYC is the capital of America! :laughing: :city_sunset:). It's a dependency which can be installed at the same time as your test framework (like tape, or mocha :coffee:).

---

### Step by step installing Istanbul 

_Pop this into command line:_

`$ npm i -D tape nyc`

_Open your package.json and make sure the scripts section looks like:_

`"scripts": {`
  `"test":     "node test.js | tap-spec",`
  `"coverage": "nyc --reporter html --reporter text npm test"`
`}`

---

_Pop this into command line:_ :lollipop:

`$ npm test`

_Once tests are run, pop this into command line:_

`$ npm run coverage`

Mocha, by default, runs tests from test/*.js. Does **tape** do the same?

---

**EGs.** _TDD/FizzBuzz Workshop_ score = :100:  :rocket:  :+1: 


![](https://i.imgur.com/U35oR3d.png) 

_TDD/FizzBuzz Workshop_ score after a test was deleted = not 100 

![](https://i.imgur.com/mMCCVvo.png)

---
