# Selenium IDE Alternative Approach

## Basic idea
Can the Gherkin tests [here](https://github.com/andreasneuber/java-cucumber-selenium-example/tree/master/src/test/resources/features) 
be converted easily into a side file for Selenium IDE?

## Application under Test
The tests fit for https://github.com/andreasneuber/automatic-test-sample-site. 
Readme in that repo has further details how to set it up.

## Usage - Run tests in Browser
- Install the Selenium IDE extension for Chrome Browser
- Open the `Sample-Project.side` project in tests/ folder
- Press the Execute button

## Usage - Run tests in Commandline runner
- Install Selenium Side Runner and Chrome Driver: `npm i`
- Then: `npm run test:visible` (When adding new tests make sure all tests belong to same suite)
- Headless: `npm run test:headless`

## Observations
- Data tables in scenario outlines can be replaced by json arrays, and looped via Selenium IDE's `for each` function
- Execution is quite fast
- Though Selenium IDE is mainly a record-and-replay tool there is some learning curve, e.g. how to execute scripts or loops
- Report is produced in JSON format, but we need to make it more human-readable

## Run in Docker
To build the Docker image execute: `docker build --no-cache -t selenium-ide-tests-docker .`

To run the tests inside the container: `docker run --rm --net="host" -it selenium-ide-tests-docker npm run test:headless`

`--net=host` is needed because the application under test is running on `http://localhost:8000`

## Links
https://www.selenium.dev/selenium-ide/docs/en/introduction/getting-started
