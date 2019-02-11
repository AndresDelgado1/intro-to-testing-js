# Intro to Testing in JS

## Summary
This is an introduction to automated testing in JavaScript. The idea behind testing is to provide feedback on the code you write to solve a problem, add a feature, or fix a bug. The feedback from the tests comes in the form of green passing tests or red failing tests. Simply, tests are functions that test functions to compare the results of the actual output vs. the expected, specified output.

## Overview
- Green tests are passing, red tests mean that the code is incomplete, inaccurate, missing, or you have a syntax error somewhere in `code.js`.
- Syntax errors in either the `tests.js` or the `code.js` file will keep things from running accurately.
- The approach of writing tests before writing the code that passes is called Test-Driven Development, or TDD.
- Writing small tests, like the ones provided, is called `unit testing`.
- "Unit testing" means to test a piece of functionality as small as a single function.
- This introduction will introduce unit tests, writing code to pass unit tests, and your very first unit tests.

## Prerequisites for this exercise
- Understanding of valid JavaScript syntax
- Data types and operators in JS
- Control statements (if, if/else, if/elseif/else, etc...)
- Authoring user defined functions
- Return data types from functions

## Getting Started
1. Fork this repository to make a copy on your own GitHub account.
1. Make sure that your browser is showing this project in your own repositories list in your own account.
1. Click the green button on the right that says "Clone or Download". 
1. The clone address should look like `git@github.com:your-github-username/intro-to-testing-js.git`, where `your-github-username` is actually your own username on GitHub.
1. Once you've copied your repo's clone address, it's time to clone the project in one of two ways: 
    - If you're using IntelliJ, choose New->Project From Version Control->Git and then paste in the clone address.`git clone git@github.com:your-github-username/intro-to-testing-js.git`.
    - If you're using command line, then execute the following command line command: `git clone git@github.com:your-github-username/intro-to-testing-js.git`.
1. Once cloned to your projects directory, open up the project.
1. Launch `report.html` in your browser. You should see a set of green tests for the `sayHello` function.
1. Refresh `report.html` to re-run new code in `test.js` or `code.js`. Do this any time the test or the implementation code changes.

### Project Structure
- The `report.html` file is the test running tool. In this case, the HTML page is loading both the `tests.js` and `code.js` files.
- The `tests.js` file contains the assertions that provide feedback on the appropriateness of the solutions in `code.js`.
- The `code.js` file contains the implementation code. An "implementation" means the code that is meant to solve a problem, fix a bug, or add a feature.

## First Exercises - look, guess, test, conclude

1. Clone this repo to your projects folder following the "Getting Started" directions. Take a moment to orient yourself with the test runner, the existing tests, and the implementation inside of `code.js`.

1. Once you're comfortable, go to `code.js` and change the name of the `helloWorld` function to `hello`. Then refresh `report.html` in your browser.
    - What do you notice about the test results?
    - What are some ways you think we could get the tests to turn green again?
    - Set the function name in `code.js` back to `helloWorld` and re-run the tests.
    
1. Inside of the `helloWorld` function in `code.js`, replace `return "Hello, World!"` with `return "Hello"`.
    - Run the tests by refreshing `report.html` in your browser.
    - Which tests fail? Which tests are still green?
    - Set the implementation back to `return "Hello, World!"`

1. Inside of the `helloWorld` function in `code.js`, change the line `return "Hello, World!"` to `console.log("Hello, World!")`. Then refresh `report.html`.
    - What happens to the tests? Identify which tests stay green and which ones turn red. 
    - Why do you think that is?
    - Consider, what is the return value of a `console.log`? *hint*, it's always the same
    - Consider, what is the return value of a `return`?
    - Fix your `helloWorld` implementation so that it greens all the tests.

1. Now, let's purposefully put a syntax error into the `helloWorld` function, to see what happens with the tests. 
    - Open up `code.js` and remove the closing curly brace from the end of the `helloWorld` function definition.
    - Refresh `report.html` in your browser.
    - Fix the syntax error and confirm that tests are all green.

1. Before moving on, ensure that all tests are green.

## Test Driven Development workflow: Tests "drive" the development.
[Test Driven Development](https://en.wikipedia.org/wiki/Test-driven_development), TDD, is the process of authoring a test before writing any other code. Here's the TDD workflow:
1. Step 1: Write the smallest possible test: Identify the simplest, smallest thing you want to confirm. For example, before a function exists, assert that the function is defined.
2. Step 2: Run all the tests to ensure that the new test fails. We're **supposed** to see a red, failing test, since there's no code yet to green it. Red means we did the first step correctly.
3. Step 3: Write only enough code to green that newest test. No more, no less.
4. Step 4: Run all tests. We're looking for green tests across the board.
5. Step 5: Refactor the code. [Refactoring](https://martinfowler.com/bliki/DefinitionOfRefactoring.html) means to increase the code quality without changing its observable behavior. This is an opportunity to increase readability, increase flexibility, reduce duplication, or make the code more accessible for yourself and other developers moving forward. 
6. Repeat.

## Let's Test Drive a `sayHello` function
- We'll build up our solution incrementally, in a Test-Driven manner.
- Ultimately, `sayHello` should say "Hello" to any string we pass to it.
- We'll worry about edge cases like "Hello, undefined!" later.

## Take your first "Test Drive" - RED -> GREEN -> REFACTOR
Our next exercise is to follow the TDD workflow to develop incremental tests and solutions for testing a `sayHello()` function that takes in a name as an argument and returns a string that says hello to that name.
- Step 1: Let's write the smallest test possible. Open up `tests.js`. Add a `describe`, an `it`, and an `expect` to assert that `sayHello` is a defined function. Use your tests for `helloWorld` as a guide. 
- Step 2: Run all the tests. At this point, we're expecting and *hoping* for a single, red failing test that we just now authored.
- Step 3: Now, let's go to `code.js` and create an empty function definition for `sayHello`.
- Step 4: Run all the tests. We're expecting all tests, including the new test for `sayHello` to be green.
- Step 5: Given that this is our first (tiny) test and our first implementation, there is not yet the opportunity to refactor.
- Step 6: Repeat (move onto the next, small test of functionality)

## Before proceeding, add your work to GitHub!
- Open your terminal and navigate to the local directory where you cloned this project. 
- First, `git status`. Notice which files are tracked by git and which files have changes.
- Second, type `git add -A` to tell git that you want to get all the changed files staged for commit. 
- Now, type `git status`. You should see file names in green. This means that the files are ready for commit.
- Next, type `git commit -m "add the first test and solution for intro-to-testing"`
- Type `git status`, again, to make sure that all files are added and committed.
- Finally, push your work by running `git push`. Pushing uploads your new commits to your remote repository, meaning your own fork on GitHub.

## Now let's make sure our function returns the right data type.
- Step 1: The smallest possible test, now that the function exists, is to ensure that calling the function gives us a string. Inside of `tests.js`, add an assertion to `sayHello` that it "should return a string when called.". The test should look similar to `expect(typeof sayHello()).toBe("string")`
- Step 2: Run all tests to make sure that the new test starts red.
- Step 3: Have your `sayHello` function return a string. The simplest code and smallest change possible is to return an empty string `return ""`. 
- Step 4: Now, run all the tests to ensure that the previously red test is now turned green by our impelementation. 
- Step 5: Still too soon to refactor...
- Step 6: Repeat (Move onto the next test)
- Always: Add, commit, and push your work to GitHub.
 
## Let's keep going w/ our TDD cycle
- Step 1: It's time to add a realistic assertion. In `tests.js`, assert that `sayHello("Jane")` returns `"Hello, Jane!"`. Our first test should be *super* simple and *super* small.
- Step 2: Run all tests and make sure that this newly added test is red.
- Step 3: If the test wants us to return `"Hello, Jane!"` then literally write `return "Hello, Jane!";` because that's the simplest way to green a test looking for `"Hello, Jane!"`.
- Step 4: Run all tests. They should all be green at this point.
- Step 5: There's nothing to refactor, yet...
- Step 6: Repeat

## Add another small, simple test and repeat the cycle
- Step 1:  In `tests.js`, assert that `sayHello("Alex")` returns `"Hello, Alex!"`. Our first test should be *super* simple and *super* small. This means that our our test should look like `expect(sayHello("Alex")).toBe("Hello, Alex!")`. 
- Step 2: Run all tests and make sure that this newly added test is red.
- Step 3: It's challenging not to jump to the "correct" answer already, but let's stay close to the method. Write *just* enough code to green the test. This means making sure that the `sayHello`  function definition inside of `code.js` takes an an input argument. If `input === "Alex"`, then we `return "Hello, Alex!"` else `return "Hello, Jane!"`. Don't get too fancy, yet. A cornerstone of TDD is refactoring only once you have a handful of green tests, not just one or two with new inputs.
- Step 4: Run all tests, expecting that all are now green. Does each test turn green? If so, then we can proceed. We can't refactor unless we have greened a test, even with a hard-coded implementation.
- Step 5: If you feel the urge to refactor already, hang on for one more test... 
- Step 6: Repeat!

## One more test before refactoring...
- Step 1: Let's add one more assertion! In `tests.js`, assert that `sayHello("Pat")` returns `"Hello, Pat!"`. Since our tests should be super simple, the assertion should be `expect(sayHello("Pat")).toBe("Hello, Pat!")`
- Step 2: Run all tests and make sure that this newly added test is red and failing. 
- Step 3: Again, you may feel the urge to jump to the "correct" answer already. Let's stay on target. Write *just* enough code to green the test. For this case, *just enough* code means adding another conditional such that if `input === "Pat"`, then the function should have `return "Hello, Pat!"`.
- Step 4: Run all tests. Does each test turn green? If so, then we can proceed. 
- Step 5: Refactor! It's definitely refactoring time!

## Refactoring
- How do we know that it's time to refactor? The answer: Once we have a handful of green tests, but the logic feels hard-coded, funky, or incomplete, then it's probably refactoring time.
- Notice that when the input is "Jane", "Pat", or "Alex", the tests green. But what if we sent in any other name as the argument? 
- If every new test means that we're adding another `if` or `else if` to the code, is there a better way of doing things?
- Refactoring is only possible once we have a handful of passing, green tests. These give us safety and guidance.
- This may feel slow, but each new test cycle should only take 2-3 minutes, if not shorter!
- Since our goal is to have a sayHello function that says hello to any input string, then all these conditionals won't fly... 
- In the TDD approach, refactoring is only possible if you have enough tests and enough code that all the tests are green. In this way, your tests provide a target for the refactor. If your refactoring fails tests that    

## Implementing the refactoring
- Inside `sayHello` in `code.js`, what's a change you can identify that will improve the overall functioning of this function?
- Can you get the implmentation of `sayHello` down to a function with only one line of code inside?
- If we have `return "Hello, " + input + "!";`, does this work for all names?
- Does this bring up any other issues?

## Repeat
- First, in `tests.js`, add `expect(sayHello()).toBe("Hello, World!")`. Then refresh `report.html` to see the failing test.
- Follow that by adding just enough code inside of the `sayHello` function `code.js` to green that latest test.
- Next, add `expect(sayHello(true)).toBe("Hello, World!")` to the `tests.js` file. Refresh to see the failing red test.
- Add just enough code to `code.js` to green that latest test.
- Now, add `expect(sayHello(false)).toBe("Hello, World!")` to the `tests.js` file. Refresh to see the failing test.
- Add just enough code to `code.js` to green this test.
- Once all the tests are green, identify more places to refactor.

## Add, commit, and push your work to GitHub.






## Let's do more TDD!

## Write out the TDD Cycle for an `isFive` function

## Write out the TDD Cycle for an `isMultipleOfThree` function

## Write out the TDD Cycle for an `isMultipleOfFive` function

## Write out the TDD Cycle for an `isVowel` function

## Write out the tests and implementation, as a full cycle for `add(a, b)` function

## Expand on the isSeven test and implementation
- Add a test that confirms if the input is the string 7
- Refresh to 
- Now