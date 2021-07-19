# Code Coveregae. 

As Aurox, we have the task of go beyond our boundaries. When we program, we are creating a new path that needs to be covered.  That's why we use software that keeps out back when we finish a new feature or we're fixing something.  Our new friend in this path it's called "Code Coverage". AKA CC (only on this page) 

## What is Code Coverage?

It's a software testing metric that determines the number of successful code lines after testing. Its company has some benefits like: 

- Easy maintenance of codebase: the report will help to ensure code quality. 
- Exposure of bad code: like unused code. 

So let's start to know how to use it on our trip. 

## Working with Code Coverage

At this point of your journey in Auronix, you must have access to your project repo here in Github If you don't have it, please let your manager know and come back :)

### coverage in the github repo

You must ensure that CC is set up on Github actions. To know it, go to your repo's workflows files and seek the following line: 

```yaml
run: vendor/bin/phpunit --coverage-clover=build/logs/clover.xml --coverage-text
```

If you find it means that we can start to cover our work.
>If you don't find the lines, don't panic. Just ask for help to know where's it or to add it.

### Testing 

There are some commands you want to know to test a feature, fix, etc. In most of the projects that use PHP, we work with PHPUnit; is a programmer-oriented testing framework, and the basic command is: 

```bash
phpunit
```

With this command, we can run all our tests in the project. 

Sometimes,  we don't want to wait for all test to run, we can filter the test to only run only one file with: 

```bash
phpunit /foo/test.php
```

There is another way to run our test and maybe the most useful for you: 

```bash
phpunit --filter test.php
```

The filter parameter can also be used to test a single function passing it the test function name:
```bash
phpunit --filter test_my_test
```
>Note: Remember to name your test correctly, starting with the word *test* and use *snake_case*  

>Another Note: Try to dont repeat names between tests, even with other test files. The command will run all the test functions whit the same name.

By default, after each test the DB gets cleaned up, If you want to debug the final state after a test you can set the DEBUG variable to true. This will prevent the DB cleanup process and let you inspect the data after you run a test. Note that with this method you must filter for a single function since running multiple tests without the DB cleanup will have side effects.


```bash
DEBUG=true phpunit --filter test_function_name

### Lets wear Coveralls

[Coveralls](https://coveralls.io/), is a web service to help you track your code coverage over time, and ensure that all your new code is fully covered. (description from page).

Coveralls will report to Github's repo automatically, you only need to make a Pull Request to run the coverage in Github Actions. After the pass the CI test, you can see the new coverage percentage on the web page.
But you can see the coverage lines in your test before doing the PR.

### Knowing Coverage in my pc

To run coverage in our device we need to set up some libs. Type in your terminal: 

```bash
sudo phpenmod xdebug
```

Then you'll be able to test with coverage by entering: 
```bash
XDEBUG_MODE=coverage phpunit --filter test --coverage-text
```
But if you are like Bob Ross, try: 
```bash
XDEBUG_MODE=coverage phpunit --filter test --coverage-html coverage
```
After running the command, you will see a new folder called coverage. Enter and open the index file, there you can see the coverage of your test with colors.
