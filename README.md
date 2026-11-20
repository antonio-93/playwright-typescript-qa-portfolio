# Playwright & TypeScript — SauceDemo Authentication Tests

## Purpose and Scope

This portfolio project demonstrates practical browser test automation using **Playwright and TypeScript** against the publicly available [SauceDemo](https://www.saucedemo.com/) training application.

This project demonstrates browser interactions, test assertions, positive and negative authentication scenarios, and test reporting.

**Scope limitation:** This is a focused demonstration against a public training application, not a production application or complete authentication test suite.

## Automated Test Coverage

| Test ID | Scenario | Expected Result |
|---|---|---|
| AUTH-01 | Login with valid credentials | User reaches the inventory page |
| AUTH-02 | Login with an incorrect password | Appropriate authentication error is displayed |
| AUTH-03 | Submit empty credentials | Required username validation is displayed |
| AUTH-04 | Logout after successful login | User returns to the login page |

The tests use SauceDemo's publicly documented demonstration credentials:

- Username: `standard_user`
- Password: `secret_sauce`

No personal credentials or private authentication data are included.

## Technology

- Playwright Test
- TypeScript
- Node.js
- Google Chrome

The test configuration uses SauceDemo as the `baseURL` and runs tests using the locally installed Google Chrome browser.

## Setup

**Prerequisites:**

- Node.js 20 or later
- Google Chrome installed

Open a terminal in the project directory and install dependencies:

```bash
npm install
```

Run the tests with the browser visible:

```bash
npm run test:headed
```

Run the tests in headless mode:

```bash
npm test
```

Open the HTML test report:

```bash
npm run report
```

Launch Playwright UI mode:

```bash
npm run test:ui
```

**Windows PowerShell note:** If PowerShell blocks `npm.ps1`, use `npm.cmd` and `npx.cmd` instead of `npm` and `npx`.

## Project Structure

```text
tests/
  login.spec.ts
playwright.config.ts
package.json
package-lock.json
README.md
.gitignore
```

## Test Design and Implementation

Each test starts from the login page using a shared `beforeEach` hook.

The tests use SauceDemo's `data-test` attributes where available, with assertions for navigation, page visibility, and authentication errors.

Playwright creates an isolated browser context for each test, reducing dependency between scenarios.

On test failure, the configuration retains a trace and captures a screenshot for troubleshooting. An HTML report is also generated.

## Limitations and Future Improvements

- The tests depend on the availability and behavior of a public demonstration website.
- The current coverage is limited to four authentication-related scenarios.
- AUTH-04 verifies navigation back to the login page; it does not independently verify server-side session invalidation.
- The tests run locally. CI integration and cross-browser execution are not included in this submission.
- A production application would require product-specific test accounts, agreed authentication and authorization rules, and additional scenarios relevant to its features.

The purpose of this project is to demonstrate a working automation approach, not to claim complete product coverage or production readiness.