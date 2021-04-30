# Testing Questions

#### What are some advantages/disadvantages to testing your code?

###### Advantages

- Prevent regression errors
- Ensure there is no missing part to change when refactoring
- Tests can be used as specs
- Test process can be shared amongst team members

###### Disadvantages: there are rarely disadvantages

- It may or may not take more time to prototype.

#### What tools would you use to test your code's functionality?

For JavaScript, the basic `assert` module is quite enough for simple tests.
But when it gets a big and production-level project, it is a better idea to
set a test framework. For backend, I usually use Mocha. For frontend, Mocha
can still be used with headless browsers such as PhantomJS. There are also
other famous tools like Selenium for browser tests.

#### What is the difference between a unit test and a functional/integration test?

- A unit test is on a small unit and checks if each unit works well.
- A functional test is on a particular feature and check if it generates a
  proper output for a provided input.
- An integration test checks if each part(or unit) of code works well together
  and results in combination functions correctly.

#### What is the purpose of a code style linting tool?

It is to keep source codes in a repository consistent and easy to read. Linting
also prevent possible mistakes developers can make. For example, some linter
provides options to check which indentation should be used(it is not actually
what a linter should do though). A linter can also check if there is any used
variable which hasn't been declared, or if there is any unused variable. In
short, linting is a kind of static analysis.

#### What is Selenium? What are the different Selenium components?

Selenium is one of the most popular automated testing suites. Selenium is designed in a way to support and encourage automation testing of functional aspects of web-based applications and a wide range of browsers and platforms. Due to its existence in the open source community, it has become one of the most accepted tools amongst the testing professionals.

Selenium is not just a single tool or a utility, rather a package of several testing tools and for the same reason, it is referred to as a Suite. Each of these tools is designed to cater different testing and test environment requirements.

The suite package constitutes the following sets of tools:

1- Selenium Integrated Development Environment (IDE)

2- Selenium Remote Control (RC)

3- Selenium WebDriver

4- Selenium Grid

https://www.softwaretestinghelp.com/selenium-interview-questions-answers/


#### What is the difference between Enzyme's rendering methods?


Jest acts as a test runner, assertion library, and mocking library.

Jest also provides Snapshot testing, the ability to create a rendered ‘snapshot’ of a component and compare it to a previously saved ‘snapshot’. The test will fail if the two do not match. Snapshots will be saved for you beside the test file that created them in an auto-generate __snapshots__ folder.

Snapshot testing must be complimented with in browser testing and looking at the snapshot created when creating the initial snapshots, to ensure that the snapshot reflects the intended outcome.

Enzyme, created by Airbnb, adds some great additional utility methods for rendering a component (or multiple components), finding elements, and interacting with elements. It must be installed in addition to tools already bundled with CRA.

Both Jest and Enzyme are specifically designed to test React applications, Jest can be used with any other Javascript app but Enzyme only works with React.

Jest can be used without Enzyme to render components and test with snapshots, Enzyme simply adds additional functionality.

Enzyme can be used without Jest, however Enzyme must be paired with another test runner if Jest is not used.

https://medium.com/codeclan/testing-react-with-jest-and-enzyme-20505fec4675

https://medium.com/@Yohanna/difference-between-enzymes-rendering-methods-f82108f49084
