# BrowserStack for Cursor

Access BrowserStack's complete testing platform directly from Cursor using natural language. Test on 3,500+ real devices and browsers, run automated tests, scan for accessibility issues, and generate test cases from requirements—all without leaving your IDE. For anything that spans several steps, hand the whole thing to Ask AI and let it plan and run the sequence for you.

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
           "BROWSERSTACK_USERNAME": "${BROWSERSTACK_USERNAME}",
           "BROWSERSTACK_ACCESS_KEY": "${BROWSERSTACK_ACCESS_KEY}"
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

- **ask-ai** - Run a multi-step workflow from a single instruction, across Test Management and Test Reporting & Analytics
- **test-failure-analysis** - Analyze test failures and get suggested fixes 
- **self-healing** - Fix flaky tests with AI-generated selectors that adapt to DOM changes
- **test-case-generator** - Generate test cases from PRD documents using AI
- **visual-review** - Summarize visual changes between the latest two Percy builds
- **visual-test-integration** - Set up Percy in your project with a full demo workflow
  
### MCP Tools (45 Available)

**Test Management**
- `createProjectOrFolder` - Create Test Management projects and folders
- `createTestCase` - Add manual test cases to projects
- `updateTestCase` - Update name, steps, priority, status, tags on an existing case
- `listTestCases` - List test cases with filters (priority, status, tags)
- `listFolders` - List folders and sub-folders in a project
- `listTestCaseTemplates` - List available test case templates
- `createTestRun` - Create test runs for selected test cases
- `listTestRuns` - List test runs with date/assignee/state filters
- `updateTestRun` - Update test run status, tags, notes, linked cases
- `addTestResult` - Add execution results (passed/failed/blocked/skipped)
- `listTestPlans` / `getTestPlan` - List and fetch test plans
- `listSubTestPlans` / `getSubTestPlan` - List and fetch sub-test-plans

**Test Reporting & Analytics**

- `getFailureLogs` - Retrieve error, console, network and device logs for a session
- `fetchBuildInsights` - Build details plus quality gate results
- `getBuildId` / `listBuildId` - Resolve a build ID from project and build name
- `listTestIds` - List test IDs from a build, filtered by status

**Automate (Web Testing)**

- `setupBrowserStackAutomateTests` - Integrate SDK and run web tests
- `fetchAutomationScreenshots` - Get screenshots from test sessions

**App Automate (Mobile Testing)**

- `setupBrowserStackAppAutomateTests` - Set up SDK for Appium-based mobile tests
- `runAppTestsOnBrowserStack` - Run Espresso/XCUITest suites on real devices
- `takeAppScreenshot` - Launch app and capture screenshot

**Live Testing**

- `runBrowserLiveSession` - Start manual browser testing session
- `runAppLiveSession` - Start manual app testing session on real devices

**Accessibility**

- `startAccessibilityScan` - Scan webpages for WCAG violations
- `fetchAccessibilityIssues` - Fetch paginated issues from a completed scan
- `accessibilityExpert` - Get WCAG guidelines and best practices
- `createAccessibilityAuthConfig` / `getAccessibilityAuthConfig` - Configure authenticated scans

**Percy (Visual Testing)**

- `expandPercyVisualTesting` - Expand Percy coverage across existing tests
- `addPercySnapshotCommands` - Add snapshot commands to test files
- `listTestFiles` - List UI test files eligible for snapshots
- `runPercyScan` - Run a Percy build
- `managePercyBuildApproval` - Approve, unapprove or reject a Percy build

**AI Agents**

- `askBrowserStackAI` - Run a multi-step Test Management or Test Reporting & Analytics workflow from a single natural-language instruction
- `fetchRCA` - Test failure analysis: insights and suggested fixes for failed tests
- `fetchSelfHealedSelectors` - Get AI-healed selectors for flaky tests
- `prepareSelfHealingPlan` - Bundle locator pairs with test source for your LLM to apply
- `uploadProductRequirementFile` - Upload PRD/PDF for test case generation
- `createTestCasesFromFile` - Bulk create test cases from an uploaded file
- `createLCASteps` - Convert manual test cases to low-code automation
- `fetchPercyChanges` - AI summary of visual changes between Percy builds
- `percyVisualTestIntegrationAgent` - Integrate Percy into a new project

## Use Cases

### 1. Run Multi-Step Workflows with Ask AI

**What**: Hand over a whole workflow in one instruction. Ask AI plans the steps, calls the required BrowserStack capabilities and returns the result. Use it when your ask spans several operations.

**Tools**: `askBrowserStackAI`

**Examples**:

```
"Find all payment test cases in project Shopping App and add the 'regression' tag to them"
"Debug my latest build, separate real failures from flaky ones, and tell me if it's safe to ship"
"Build me a dashboard showing flaky % by team for the last 30 days"
```

**What you get**:

- The steps planned and executed in sequence, not a single tool call
- Currently covers Test Management and Test Reporting & Analytics, with support for more products coming soon
- Requires an active Test Management or Test Reporting & Analytics license

---

### 2. Generate Test Cases from Requirements

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

### 3. Manage Test Cases and Runs

**What**: Organize test cases, create test runs, and track results.

**Tools**: `createProjectOrFolder`, `createTestCase`, `updateTestCase`, `listTestCases`, `listFolders`, `createTestRun`, `addTestResult`, `listTestPlans`

**Examples**:

```
"Create a Test Management project called 'Payment Flow'"
"Add a test case: Verify credit card payment with invalid CVV"
"List all high priority test cases in Payment Flow"
"Create a test run for smoke tests"
"Mark test case TC-123 as passed"
"Show me the test plans in project PR-12345"
```

---

### 4. Manual Testing on Real Devices

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

### 5. Run Automated Web Tests

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

### 6. Run Automated Mobile App Tests

**What**: Execute Appium, XCUITest, or Espresso tests on real iOS and Android devices.

**Skill**: `run-mobile-tests-on-browserstack`

**Tools**: `setupBrowserStackAppAutomateTests`, `takeAppScreenshot`, `runAppTestsOnBrowserStack`, `getFailureLogs`

**Examples**:

```
"Take a screenshot of my app on iPhone 15 Pro. App: /apps/myapp.ipa"
"Run Espresso tests on Galaxy S21 and Pixel 6. App: /apps/app.apk, Tests: /tests/suite.zip"
"Run XCUITest tests on iPhone 14 and 15 Pro with iOS 17. Tests: /tests/login.zip"
"Get error logs from App Automate session abc123, Build ID xyz789"
```

---

### 7. Auto-Heal Flaky Tests

**What**: Fix test failures caused by changed selectors using the self-healing agent.

**Tools**: `fetchSelfHealedSelectors`, `prepareSelfHealingPlan`

**Examples**:

```
"My login test keeps failing because the button selector changed. Fix it with self-healing."
"Get self-healed selectors for session session_abc123"
"Prepare a self-healing plan for my latest build"
```

---

### 8. Scan and Fix Accessibility Issues

**What**: Identify WCAG violations on your webpage and get specific code fixes.

**Skill**: `scan-and-fix-accessibility`

**Tools**: `startAccessibilityScan`, `fetchAccessibilityIssues`, `accessibilityExpert`, `createAccessibilityAuthConfig`

**Examples**:

```
"Run accessibility scan for 'localhost:3000'"
"Scan accessibility issues on www.mysite.com/checkout"
"What WCAG guidelines apply to form field error messages?"
"Set up an authenticated scan for my staging site"
"Re-scan localhost:3000 to verify fixes"
```

**What you get**:

- Detailed violation report (Critical/High/Medium severity)
- Specific code fixes for each issue (missing labels, color contrast, keyboard navigation)
- WCAG compliance verification after fixes

---

### 9. Debug Failing Builds

**What**: Find what failed, run test failure analysis, and separate real product bugs from broken automation.

**Tools**: `getBuildId`, `listBuildId`, `listTestIds`, `fetchRCA`, `getFailureLogs`, `fetchBuildInsights`

**Examples**:

```
"Get the build ID for 'nightly-regression' in project Checkout Flow"
"List the failed tests from my latest build"
"Fetch root cause analysis for test IDs 101 and 102"
"Get console and network logs from session abc123"
"Show me quality gate results for this build"
```

**What you get**:

- Failed tests isolated from the rest of the build
- Analysis with a suggested fix, presented as a proposal only — never applied automatically

---

### 10. Catch Visual Regressions with Percy

**What**: Add visual testing to an existing suite, run scans, and review what changed between builds.

**Tools**: `percyVisualTestIntegrationAgent`, `expandPercyVisualTesting`, `addPercySnapshotCommands`, `listTestFiles`, `runPercyScan`, `fetchPercyChanges`, `managePercyBuildApproval`

**Examples**:

```
"Integrate Percy into this project"
"Expand Percy coverage across my Playwright tests"
"Run a Percy scan for project shop-web"
"What changed visually in the latest Percy build?"
"Approve the latest Percy build"
```

**What you get**:

- Percy wired into your existing test suite, with snapshot commands added for you
- An AI summary of what changed between the latest build and the previous one

## Troubleshooting

**Authentication Issues**

- Verify credentials in [Account Settings](https://www.browserstack.com/accounts/profile/details)
- Check MCP configuration in Cursor settings
- Ensure no extra spaces in username/access key

**Plugin Not Responding**

- Restart Cursor after configuration changes
- Check Node.js version: `node --version` (need 18+)
- View MCP server logs in Cursor

**A Tool Isn't Available**

- AI agent tools require AI preferences to be activated on your account. See [activate BrowserStack AI](https://www.browserstack.com/docs/iaam/settings-and-permissions/activate-browserstack-ai).
- Some tools require an active license for the corresponding product (Test Management, Test Reporting & Analytics, Percy, Accessibility). Contact [BrowserStack Support](https://www.browserstack.com/contact) to enable one.
- Make sure your config uses `@browserstack/mcp-server@latest`. A pinned version will not pick up newly released tools.

**Need Help?**

- [GitHub Issues](https://github.com/browserstack/mcp-server/issues) - Report bugs or issues
- [BrowserStack Support](https://www.browserstack.com/contact) - Platform questions
- [Documentation](https://www.browserstack.com/docs/browserstack-mcp-server/tools) - Full tool reference and workflows

---

## How to Sign Up for BrowserStack?

1. **Create a free account** at [browserstack.com/users/sign_up](https://www.browserstack.com/users/sign_up)

   - No credit card required
   - Instant access to start testing

2. **Get your credentials** from [Account Settings](https://www.browserstack.com/accounts/profile/details) to configure the plugin
