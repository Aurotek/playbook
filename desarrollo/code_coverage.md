# Code Coveregae. 

As Aurox, we have the task of go beyond our boundaries. When we program, we are creating a new path that needs to be covered.  That's why we use software that keeps out back when we finish a new feature or we're fixing something.  Our new friend in this path it's called "Code Coverage". AKA CC (only on this page) 

## who is Code Coverage?

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

There is some command you want to know to test a feature, test, etc. In most of the projects that use PHP, we work with PHPUnit; is a programmer-oriented testing framework, and the basic command is: 

```bash
phpunit
```

With this command, we can run all our tests in the project. But we don't want to wait until our new test appears in the list to know if our code pass.  To only run our tests we can use: 

```bash
phpunit /foo/test.php
```

There is another way to run our test and maybe the most useful for you: 

```bash
phpunit --filter test.php
```

Whit this command you only can test your file also can test a single test functión. Only need to type the test function name:
```bash
phpunit --filtes test_my_test
```
>Note: Remember to name your test correctly, starting with the word *test* and use *snake_case*  

>Another Note: Try to dont repeat names between tests, even with other test files. The command will run all the test functions whit the same name.

Sometimes DB requests are needed. But the test projects seed the DB test, which means our changes won't last after our test. To see our changes in DB we can use: 
```bash
DEBUG=true phpunit --filter test
```

### Lets wear Coveralls

[Coveralls](https://coveralls.io/), is a web service to help you track your code coverage over time, and ensure that all your new code is fully covered. (description from page).

Coveralls will report to Github's repo automatically, you only need to make a Pull Request to run the coverage in Github Actions. After the pass the CI test, you can see the new coverage percentage on the web page.
But you can see the coverage lines in your test before doing the PR.

### Knowing Coverage in my pc

To run coverage in our device we need to set up some libs. Type in your terminal: 

```bash
sudo phpenmod xdebug
```

Then you be able to test with coverage by entering: 
```bash
XDEBUG_MODE=coverage phpunit --filter test --coverage-text
```
But if you are like Bob Ross, try: 
```bash
XDEBUG_MODE=coverage phpunit --filter test --coverage-html coverage
```
After running the command, you will see a new folder called coverage. Enter and open the index file, there you can see the coverage of your test with colors.
