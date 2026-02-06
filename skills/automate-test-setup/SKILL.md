---
name: automate-test-setup
description: Set up and run automated web tests on BrowserStack Automate. Use for cross-browser testing, CI/CD integration, or running existing Selenium/Playwright/Cypress tests on real browsers.
---

# Automate Test Setup Workflow

## When to Use

- Running web tests across multiple browsers
- Setting up CI/CD pipeline with BrowserStack
- Testing on real desktop browsers (Chrome, Firefox, Safari, Edge)
- Debugging cross-browser compatibility issues

## Steps

### 1. Get Available Browsers

List all browsers and OS combinations:
```
"Show me available browsers on BrowserStack Automate"
```

### 2. Configure Test

Choose your test framework and configuration:

**For Selenium (Java/Python/Node.js):**
```
"Help me set up Selenium tests for BrowserStack Automate"
```

**For Playwright:**
```
"Configure Playwright to run on BrowserStack"
```

**For Cypress:**
```
"Set up Cypress for BrowserStack Automate"
```

### 3. Set Browser Capabilities

Specify which browsers to test on:
```
"I want to test on Chrome 120 (Windows 11) and Safari 17 (macOS Sonoma)"
```

The agent will help configure capabilities like:
```json
{
  "browserName": "Chrome",
  "browserVersion": "120",
  "os": "Windows",
  "osVersion": "11"
}
```

### 4. Run Tests

Execute your test suite:
```
"Run my tests on BrowserStack Automate"
```

Or run specific tests:
```
"Run login.test.js on Chrome and Firefox"
```

### 5. View Results

Check test execution results:
```
"Show me the latest Automate test results"
"Get the session recording for the last test run"
```

## Common Scenarios

**Parallel Testing:**
```
"Run tests in parallel across 5 browsers"
```

**Debugging Failed Tests:**
```
"Show me console logs and network logs for the failed test"
"Get screenshots from the test session"
```

**Local Testing:**
```
"Set up BrowserStack Local for testing localhost"
```

## Example

**User**: "I need to test my checkout flow on Chrome, Firefox, and Safari"

**Workflow**:
1. Get browsers: `"Show available browsers on Automate"`
2. Configure: `"Set up Selenium tests for Chrome 120, Firefox 122, Safari 17"`
3. Run: `"Run checkout.test.js on all three browsers"`
4. Results: `"Show me test results and any failures"`
5. Debug: If failures → `"Get screenshots and logs for failed tests"`

## Quick Tips

- Use parallel testing to speed up execution
- Enable video recording for debugging
- Set up BrowserStack Local for testing internal environments
- Use tags to organize test runs
- Check the Automate dashboard for detailed reports
