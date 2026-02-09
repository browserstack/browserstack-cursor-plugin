# BrowserStack for Cursor

Access BrowserStack's complete testing platform directly from Cursor using natural language. Test on 3,500+ real devices and browsers, run automated tests, scan for accessibility issues, and generate test cases from requirements—all without leaving your IDE.

## Getting Started

### Prerequisites

- Node.js 18 or higher ([download](https://nodejs.org/en/download))
- BrowserStack account ([sign up for free trial](https://www.browserstack.com/users/sign_up))

### Installation

1. **Get your BrowserStack credentials** from [Account Settings](https://www.browserstack.com/accounts/profile/details)

2. **Configure MCP settings in Cursor**:
   - Open Cursor Settings
   - Navigate to MCP configuration
   - Add BrowserStack credentials:

   ```json
   {
     "mcpServers": {
       "browserstack": {
         "command": "npx",
         "args": ["-y", "@browserstack/mcp-server@latest"],
         "env": {
           "BROWSERSTACK_USERNAME": "your_username",
           "BROWSERSTACK_ACCESS_KEY": "your_access_key"
         }
       }
     }
   }
   ```

3. **Restart Cursor** and verify:
   ```
   "Open google.com on Chrome"
   ```

## What's Included

### Skills

- **scan-and-fix-accessibility** - Scan webpages for WCAG violations and get code fixes
- **run-web-tests-on-browserstack** - Run Selenium/Playwright/Cypress tests on multiple browsers
- **run-mobile-tests-on-browserstack** - Run Appium/XCUITest/Espresso tests on real devices

### Agents

- **test-case-generator** - Generate test cases from PRD documents using AI

### MCP Tools (20 Available)

**Test Management**
- `createProjectOrFolder` - Create Test Management projects and folders
- `createTestCase` - Add manual test cases to projects
- `listTestCases` - List test cases with filters (priority, status, tags)
- `createTestRun` - Create test runs for selected test cases
- `listTestRuns` - List test runs with date/assignee filters
- `updateTestRun` - Update test run status, tags, notes
- `addTestResult` - Add execution results (passed/failed/blocked/skipped)
- `createTestCasesFromFile` - Bulk create test cases from uploaded files

**Automate (Web Testing)**
- `setupBrowserStackAutomateTests` - Integrate SDK and run web tests
- `fetchAutomationScreenshots` - Get screenshots from test sessions
- `getFailureLogs` - Retrieve error logs for failed tests

**App Automate (Mobile Testing)**
- `takeAppScreenshot` - Launch app and capture screenshot
- `runAppTestsOnBrowserStack` - Run automated mobile tests on real devices

**Live Testing**
- `runBrowserLiveSession` - Start manual browser testing session
- `runAppLiveSession` - Start manual app testing session on real devices

**Accessibility**
- `startAccessibilityScan` - Scan webpages for WCAG violations
- `accessibilityExpert` - Get WCAG guidelines and best practices

**AI Agents**
- `uploadProductRequirementFile` - Upload PRD/PDF for test case generation
- `fetchSelfHealedSelectors` - Get AI-healed selectors for flaky tests
- `createLCASteps` - Convert manual test cases to low-code automation

## Use Cases

### 1. Generate Test Cases from Requirements

**What**: Upload PRD documents and automatically generate comprehensive test cases with AI.

**Agent**: `test-case-generator` (invoke with `@test-case-generator`)

**Tools**: `uploadProductRequirementFile`, `createTestCasesFromFile`

**Examples**:
```
@test-case-generator
[Attach your PRD file]
"Generate test cases for Test Management project PR-12345"

@test-case-generator
"Upload PRD from /Users/xyz/login-flow.pdf and generate test cases for project PR-54321"
```

**What you get**:
- Test cases with title, steps, expected results, priority, and tags
- Automatically added to your Test Management project (PR-xxxxx format)
- Coverage of happy paths, error scenarios, edge cases, security

---

### 2. Manage Test Cases and Runs

**What**: Organize test cases, create test runs, and track results.

**Tools**: `createProjectOrFolder`, `createTestCase`, `listTestCases`, `createTestRun`, `addTestResult`

**Examples**:
```
"Create a Test Management project called 'Payment Flow'"
"Add a test case: Verify credit card payment with invalid CVV"
"List all high priority test cases in Payment Flow"
"Create a test run for smoke tests"
"Mark test case TC-123 as passed"
```

---

### 3. Manual Testing on Real Devices

**What**: Test your website or app on real browsers and devices on BrowserStack

**Tools**: `runBrowserLiveSession`, `runAppLiveSession`

**Examples**:
```
"Open localhost:3000 on Safari 17"
"Test my website on Chrome 120 Windows 11"
"Open my app on iPhone 15 Pro Max. App: /path/to/app.ipa"
"Take a screenshot of the current page"
```

---

### 4. Run Automated Web Tests

**What**: Execute Selenium, Playwright, or Cypress tests across multiple browsers on BrowserStack infrastructure.

**Skill**: `run-web-tests-on-browserstack`

**Tools**: `setupBrowserStackAutomateTests`, `fetchAutomationScreenshots`, `getFailureLogs`

**Examples**:
```
"Run my Playwright tests on Chrome and Firefox using BrowserStack"
"Setup my Selenium tests for BrowserStack and run on Safari 17"
"Run my Cypress tests on Chrome 120 and Edge. Enable Percy."
"Get screenshots from Automate session abc123xyz"
"Get error logs from session ID 21a864032a7459f1e7634222249b316759d6827f"
```

---

### 5. Run Automated Mobile App Tests

**What**: Execute Appium, XCUITest, or Espresso tests on real iOS and Android devices.

**Skill**: `run-mobile-tests-on-browserstack`

**Tools**: `takeAppScreenshot`, `runAppTestsOnBrowserStack`, `getFailureLogs`

**Examples**:
```
"Take a screenshot of my app on iPhone 15 Pro. App: /apps/myapp.ipa"
"Run Espresso tests on Galaxy S21 and Pixel 6. App: /apps/app.apk, Tests: /tests/suite.zip"
"Run XCUITest tests on iPhone 14 and 15 Pro with iOS 17. Tests: /tests/login.zip"
"Get error logs from App Automate session abc123, Build ID xyz789"
```

---

### 6. Auto-Heal Flaky Tests

**What**: Fix test failures caused by changed selectors using AI self-healing.

**Tools**: `fetchSelfHealedSelectors`

**Examples**:
```
"My login test keeps failing because the button selector changed. Fix it with self-healing."
"Get self-healed selectors for session session_abc123"
```

---

### 7. Scan and Fix Accessibility Issues

**What**: Identify WCAG violations on your webpage and get specific code fixes.

**Skill**: `scan-and-fix-accessibility`

**Tools**: `startAccessibilityScan`, `accessibilityExpert`

**Examples**:
```
"Run accessibility scan for 'localhost:3000'"
"Scan accessibility issues on www.mysite.com/checkout"
"What WCAG guidelines apply to form field error messages?"
"Re-scan localhost:3000 to verify fixes"
```

**What you get**:
- Detailed violation report (Critical/High/Medium severity)
- Specific code fixes for each issue (missing labels, color contrast, keyboard navigation)
- WCAG compliance verification after fixes

## Troubleshooting

**Authentication Issues**
- Verify credentials in [Account Settings](https://www.browserstack.com/accounts/profile/details)
- Check MCP configuration in Cursor settings
- Ensure no extra spaces in username/access key

**Plugin Not Responding**
- Restart Cursor after configuration changes
- Check Node.js version: `node --version` (need 18+)
- View MCP server logs in Cursor

**Need Help?**
- [GitHub Issues](https://github.com/browserstack/mcp-server/issues) - Report bugs or issues
- [BrowserStack Support](https://www.browserstack.com/contact) - Platform questions
- [Documentation](https://www.browserstack.com/docs) - Detailed guides

---

## Pricing

- **Free Trial** - Get started with limited minutes ([sign up](https://www.browserstack.com/users/sign_up))
- **Open Source** - Free access for qualifying projects ([apply](https://www.browserstack.com/open-source))
- **Paid Plans** - From $29/month ([view pricing](https://www.browserstack.com/pricing))
