# BrowserStack for Cursor

Test websites and mobile apps on 3,500+ real devices and browsers directly from Cursor using natural language.

## What You Can Do

- Test localhost on iPhone 15 Pro Max or Safari 17 without owning a Mac
- Debug app crashes on Android 14 in real-time
- Run Playwright/Selenium tests on 50+ browser/OS combinations
- Generate test cases from PRD documents with AI
- Scan and fix accessibility issues (WCAG compliance)
- Auto-heal flaky tests

## Setup

**Requirements**: Node.js 18+ ([download](https://nodejs.org/en/download))

1. **Get BrowserStack credentials** from [Account Settings](https://www.browserstack.com/accounts/profile/details)
   - Free trial available ([sign up](https://www.browserstack.com/users/sign_up))

2. **Add to environment**:
   ```bash
   # macOS/Linux
   export BROWSERSTACK_USERNAME="your_username"
   export BROWSERSTACK_ACCESS_KEY="your_access_key"
   
   # Windows PowerShell
   $env:BROWSERSTACK_USERNAME="your_username"
   $env:BROWSERSTACK_ACCESS_KEY="your_access_key"
   ```

3. **Restart Cursor** and test: `"Open google.com on Chrome"`

## Common Workflows

### 🚀 Quick Manual Testing

Testing your local development site on different browsers:

```
💬 "Open my website running on localhost:3000 on Safari 17"
💬 "Test localhost:8080 on the latest Chrome on Windows 11"
💬 "Open my site on Firefox on macOS"
💬 "Take a screenshot of this page"
```

**Use case**: You're developing a feature and need to check if it works on Safari, but you're on Windows.

---

### 📱 Mobile App Testing

Test your mobile app on real devices:

```
💬 "Open my app on iPhone 15 Pro Max"
   (Cursor will ask for your .ipa or .apk file path)

💬 "Test my app on Galaxy S24 with Android 14"
💬 "My app crashes on iOS 17 when I tap the login button, help me debug"
```

**Use case**: You don't have physical access to an iPhone 15 Pro Max but need to verify the login flow works.

---

### 🧪 Running Automated Tests

Run your existing test suite on BrowserStack (uses **Automate Test Setup** and **App Automate Test Setup** skills):

**Web tests:**
```
💬 "Setup my Playwright tests to run on BrowserStack"
💬 "Run my tests on Chrome, Firefox, and Safari"
💬 "Show me available browsers on Automate"
```
Quick Examples

**Manual Testing**
```
"Open localhost:3000 on Safari 17"
"Test my app on iPhone 15 Pro. App: /path/to/app.ipa"
"Take a screenshot"
```

**Automated Testing**
```
"Run my Playwright tests on Chrome and Firefox"
"Run Espresso tests on Galaxy S21. App: /app.apk, Tests: /tests.zip"
```

**Accessibility**
```
"Scan accessibility issues on localhost:3000"
"What WCAG guidelines apply to form error messages?"
```

**AI Testing**
```
@test-case-generator [attach PRD]
"Generate test cases for project PR-12345"
```

**Test Management**
```
"Create Test Management project 'Payment Flow'"
"Add test case: Verify credit card payment with invalid CVV"
"Mark test case TC-123 as passed
```

---

#### Automate Test Setup
**What it does**: Integrates your web test framework with BrowserStack and runs tests across multiple browsers automatically.

**When to use**: Running Selenium/Playwright/Cypress tests, CI/CD integration, cross-browser testing.

**Sample commands**:
```
💬 "Run my Selenium tests on Chrome and Firefox using BrowserStack"
💬 "Setup my Playwright tests for BrowserStack and run on Safari 17"
💬 "Run my Cypress tests on Chrome 120 and Edge. Enable Percy."
💬 "Get screenshots from Automate session abc123xyz"
```

**What happens**:
1. Integrates BrowserStack SDK into your test framework
2. Configures tests to run on specified browsers/OS combinations
3. Runs tests on BrowserStack infrastructure
4. Returns session IDs and test results
5. Provides screenshots and error logs for debugging

**Example**:
```
💬 "Run my Selenium-JUnit5 tests written in Java on Chrome and Firefox. Enable Percy for visual testing."

✓ BrowserStack SDK integrated
✓ Tests running on Chrome 120, Firefox 122
✓ Percy visual testing enabled
✓ Session IDs: session_abc123, session_xyz789
```

---

#### App Automate Test Setup
**What it does**: Sets up and runs automated mobile app tests on BrowserStack App Automate using `runAppTestsOnBrowserStack` and `takeAppScreenshot` MCP tools.

**When to use**: TRuns automated mobile app tests on real iOS and Android devices using your test framework (Appium/XCUITest/Espresso).

**When to use**: Testing mobile apps, device matrix testing, mobile CI/CD integration.

**Sample commands**:
```
💬 "Take a screenshot of my app on iPhone 15 Pro. App: /apps/myapp.ipa"
💬 "Run Espresso tests on Galaxy S21 and Pixel 6. App: /apps/app.apk, Tests: /tests/suite.zip"
💬 "Run XCUITest tests on iPhone 14 and 15 Pro with iOS 17. Tests: /tests/login.zip"
💬 "Get error logs from App Automate session abc123"
```

**What happens**:
1. Uploads your app (.ipa or .apk) to BrowserStack
2. Uploads your test suite
3. Runs tests on specified real devices
4. Returns session IDs, test results, and logs
5. Provides error logs and crash reports for debugging
```
💬 "Run Espresso tests from /tests/checkout.zip on Galaxy S21. App: /apps/beta.apk"

✓ App uploaded: bs://abc123xyz
✓ Test suite uploaded
✓ Running Espresso tests on Samsung Galaxy S21 (Android 12)
✓ Session ID: session_xyz789
✓ Build ID: build_abc123
```

---

### 🤖 AI Agent

#### Test Case Generator
**What it does**: Generates comprehensive test cases from PRD documents using `uploadProductRequirementFile` and `createTestCasesFromFile` MCP tools.

**When to use**: PAnalyzes your product requirements and automatically generates comprehensive test cases, adding them to your Test Management project.

**When to use**: Planning new features, creating test suites, converting requirements to structured test cases.

**Sample commands**:
```
💬 @test-case-generator
   [Add your PRD file or requirements document to context]
   "Generate test cases for Test Management project PR-12345"

💬 @test-case-generator
   "Upload PRD from /Users/xyz/login-flow.pdf and generate test cases for project PR-54321"
```

**What happens**:
1. Uploads and analyzes your PRD, PDF, or requirements document
2. AI generates structured test cases with steps and expected results
3. Test cases automatically added to your Test Management project (format: 
- Test case title and description
- Priority level (Critical/High/Medium/Low)
- Preconditions
- Step-by-step test steps
- Expected results
- Appropriate tags (@smoke, @regression, @p0, etc.)

**Example interaction**:
```
You: @test-case-generator
     [Attach: login-feature-spec.pdf]
     "Generate test cases for project PR-12345"

Agent: ✓ PRD uploaded and analyzed
       ✓ Generated 6 test cases:
       
       • TC-001: Login - Valid Credentials - Success (@smoke, @p0)
       • TC-002: Login - Invalid Password - Error (@regression, @p1)
       • TC-003: Login - Google OAuth - Success (@smoke, @p0)
       • TC-004: Login - Empty Fields - Validation (@regression, @p2)
       • TC-005: Login - Unregistered Email - Error (@regression, @p1)
       • TC-006: Login - SQL Injection Prevention (@security, @p1)
       
       All test cases added to Test Management project PR-12345
```

---

## Real Examples

### Example 1: Cross-Browser Bug Fix

**Scenario**: Users report a broken layout on Safari.

```
💬 "Open localhost:3000/dashboard on Safari 17 on macOS Sonoma"
   → BrowserStack opens a real Safari session
   → You see the layout is indeed broken
   
💬 "Take a screenshot of this page"
   → Screenshot saved to your project
   
💬 "Now open the same page on Chrome to compare"
   → Opens Chrome session
   → Layout works fine
   
💬 "What CSS properties might cause this Safari-specific issue?"
   → Cursor analyzes your code and suggests the problem
```

### Example 2: Mobile App Crash Debug

**Scenario**: Your iOS app crashes on launch for some users.

```
💬 "Open my app on iPhone 14 with iOS 16"
   (Provide path: /Users/me/builds/app-v2.1.ipa)
   → App launches successfully
   
💬 "Try on iPhone 15 with iOS 17"
   → App crashes!
   
💬 "Get the crash logs for this session"
   → Cursor retrieves logs
   
💬 "Analyze these crash logs and suggest a fix"
   → Cursor identifies the issue and suggests code changes
```

### Example 3: Automated Test Failure Investigation

**Scenario**: Your CI pipeline shows test failures on BrowserStack.

```
💬 "My Automate build 'feature-branch-123' has 3 failed tests. What went wrong?"
   → Cursor fetches error logs and screenshots
   
💬 "Show me screenshots from the failed tests"
   → Screenshots displayed
   
💬 "The login button selector seems wrong. Update my test file with the correct selector."
   → Cursor updates your test file
   
💬 "Re-run the tests"
   → Tests pass ✅
```

## What's Available

**Manual Testing**
- Test websites on any browser/OS combination
- Test mobile apps on 3,500+ real devices
- Access localhost from cloud devices (no deployment needed)

**Automated Testing**  
- Run Playwright, Selenium, Cypress, and more
- Parallel test execution across browsers
- Get screenshots, videos, and logs automatically

**Test Management**
- Create and organize test cases
- Track test execution and results
- Generate test reports

**Accessibility Testing**
- WCAG 2.0/2.1/2.2 compliance scanning
- AI-powered fix suggestions
- Local and production site scanning

**AI-Powered Features**
- Generate test cases from requirements documents
- Auto-heal flaky test selectors
- Convert manual tests to automation
- Intelligent failure analysis and debugging

## Troubleshooting

**Plugin not responding?**
- Verify your credentials are set correctly: `echo $BROWSERSTACK_USERNAME`
- Restart Cursor after adding credentials
- Check Node.js version: `node --version` (need 18+)

**"Authentication failed" error?**
- Double-check your username and access key from [Account Settings](https://www.browserstack.com/accounts/profile/details)
- Make sure there are no extra spaces in your environment variables

**Can't access localhost?**
- This works automatically! Just use `localhost:PORT` in your prompts
- BrowserStack creates a secure tunnel to your local machine

**Behind a corporate firewall?**
- Contact your IT team to allowlist BrowserStack domains
- Or ask us about enterprise firewall configurations

## Get Help

- **Issues with the plugin**: [Open a GitHub issue](https://github.com/browserstack/mcp-server/issues)
- **BrowserStack platform questions**: [Contact Support](https://www.browserstack.com/contact)
- **Documentation**: [BrowserStack Docs](https://www.browserstack.com/docs)

## Pricing

- **Free Trial**: Test drive with limited minutes
- **Open Source**: Free for qualifying projects ([apply here](https://www.browserstack.com/open-source))
- **Paid Plans**: From $29/month for individuals, custom enterprise pricing

See [pricing details](https://www.browserstack.com/pricing)
- **Authentication failed?** Check credentials in [Account Settings](https://www.browserstack.com/accounts/profile/details)
- **Plugin not responding?** Verify `echo $BROWSERSTACK_USERNAME` and restart Cursor
- **Need help?** [GitHub Issues](https://github.com/browserstack/mcp-server/issues) | [Support](https://www.browserstack.com/contactAvailable ([sign up](https://www.browserstack.com/users/sign_up))
- **Open Source**: Free ([apply](https://www.browserstack.com/open-source))
- **Paid**: From $29/month ([details](https://www.browserstack.com/pricing)