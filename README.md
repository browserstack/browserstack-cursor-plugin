# BrowserStack for Cursor

Test websites and mobile apps on 3,500+ real devices and browsers—directly from Cursor using natural language. No context switching and very easy to setup.

## What You Can Do

**Test anywhere, from anywhere**
- Open your localhost app on an iPhone 15 Pro Max
- Test your website on Safari 17 without owning a Mac
- Debug app crashes on Android 14 in real-time
- Run Playwright tests on 50+ browser/OS combinations

**Stay in your flow**
- Ask in plain English: *"Test my site on Edge"*
- Get instant access to real devices
- Debug failed tests without leaving Cursor
- Fix accessibility issues with AI suggestions

**Automate everything**
- Run test suites on BrowserStack infrastructure
- Generate test cases from product requirements
- Auto-heal flaky tests with AI
- Manage test cases and track results

## Setup

### Step 1: Install Node.js

You need Node.js version 18 or higher (we recommend v22.15.0 LTS).

Check your version:
```bash
node --version
```

If you need to install or update:
- **macOS**: `brew update && brew upgrade node` or [download here](https://nodejs.org/en/download)
- **Windows**: Download from [nodejs.org](https://nodejs.org/en/download)

### Step 2: Get BrowserStack Credentials

1. **Sign up** at [browserstack.com/users/sign_up](https://www.browserstack.com/users/sign_up)
   - Free trial available, no credit card required
   - Open source projects get free access

2. **Get your credentials** from [Account Settings](https://www.browserstack.com/accounts/profile/details)
   - You'll need your `Username` and `Access Key`
   - Keep these handy for the next step

### Step 3: Install the Plugin

1. **Install from Cursor Marketplace** (or manually)

2. **Add your credentials** to your environment:

   **On macOS/Linux:**
   ```bash
   # Open your shell profile
   nano ~/.zshrc  # or ~/.bashrc if you use bash
   
   # Add these lines at the end (replace with your actual credentials)
   export BROWSERSTACK_USERNAME="your_username_here"
   export BROWSERSTACK_ACCESS_KEY="your_access_key_here"
   
   # Save and reload
   source ~/.zshrc
   ```

   **On Windows (PowerShell):**
   ```powershell
   # Open PowerShell profile
   notepad $PROFILE
   
   # Add these lines
   $env:BROWSERSTACK_USERNAME="your_username_here"
   $env:BROWSERSTACK_ACCESS_KEY="your_access_key_here"
   ```

3. **Restart Cursor** to activate the plugin

4. **Verify installation** by asking Cursor:
   ```
   "Open google.com on Chrome"
   ```

✅ That's it! You're ready to test.

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

**Mobile app tests:**
```
💬 "Upload my app to BrowserStack"
💬 "Set up Appium tests for iPhone 15 and Galaxy S24"
💬 "Run my app tests on top 10 Android devices"
```

**Workflow example**:
1. You: *"Setup my Playwright tests to run on BrowserStack"*
2. Cursor configures your test framework with BrowserStack capabilities
3. You: *"Run my tests on Chrome and Edge"*
4. BrowserStack runs your tests in parallel
5. View results, session recordings, and logs
6. If tests fail: *"Help me debug the failures"*

---

### ♿ Accessibility Scanning

Catch accessibility issues before production (uses **Accessibility Fix** skill):

```
💬 "Scan accessibility issues on localhost:3000"
💬 "Fix accessibility problems on my checkout page"
💬 "Check WCAG 2.1 AA compliance for my signup form"
```

**Use case**: You want to ensure your signup form is accessible before deploying.

**What happens**: The skill scans your page, identifies violations, provides specific code fixes, and verifies after you implement them.

---

### 📋 Test Case Management

Organize and track your testing:

```
💬 "Create a Test Management project called 'Payment Flow'"
💬 "Add a test case: Verify credit card payment with invalid CVV"
💬 "List all high priority test cases in Payment Flow"
💬 "Create a test run for smoke tests"
💬 "Mark test case TC-123 as passed"
```

**Workflow example**:
1. Create project structure
2. Add test cases as you develop features
3. Create test runs before releases
4. Track results and generate reports

---

### 🤖 AI-Powered Testing

**Generate test cases from requirements** (uses **Test Case Generator** agent):
```
💬 @test-case-generator
   [Attach your PRD file]
   "Generate test cases for project PR-12345"
   
💬 @test-case-generator
   "Create test cases for checkout flow with credit card and PayPal"
   "Add to project PR-67890"
```

**Auto-heal flaky tests:**
```
💬 "My login test keeps failing because the button selector changed. Fix it with self-healing."
💬 "Get self-healed selectors for session session_abc123"
```

**Convert manual tests to automation:**
```
💬 "Convert my manual test case TC-45 into a Playwright script"
```

---

## Built-in Skills & Agents

The plugin includes specialized workflows and AI agents to streamline common testing tasks.

### 🔧 Skills (Multi-Step Workflows)

#### Accessibility Fix
**What it does**: Scans your page for WCAG violations, identifies issues, and provides code fixes.

**When to use**: Before deployment, fixing accessibility bugs, ensuring compliance.

**Sample commands**:
```
💬 "Scan accessibility issues on localhost:3000"
💬 "Fix the accessibility problems on my checkout page"
💬 "Check WCAG 2.1 AA compliance for localhost:8080/signup"
```

**Workflow**:
1. Runs accessibility scan on your page
2. Categorizes issues (Critical/High/Medium)
3. Provides specific code fixes for each issue
4. Re-scans after you implement fixes to verify

**Example fix output**:
```html
<!-- Missing form label fix -->
<!-- Before -->
<input type="email" placeholder="Email">

<!-- After -->
<label for="email">Email Address</label>
<input type="email" id="email" aria-required="true">
```

---

#### Automate Test Setup
**What it does**: Sets up and runs automated web tests on BrowserStack Automate across multiple browsers and OS combinations.

**When to use**: Running Selenium/Playwright/Cypress tests, CI/CD integration, cross-browser testing.

**Sample commands**:
```
💬 "Set up Playwright tests for BrowserStack Automate"
💬 "Run my tests on Chrome 120, Firefox 122, and Safari 17"
💬 "Show me available browsers on BrowserStack Automate"
💬 "Run checkout.test.js in parallel on 5 browsers"
```

**Workflow**:
1. Lists available browsers and OS combinations
2. Helps configure your test framework (Selenium/Playwright/Cypress)
3. Sets browser capabilities for target platforms
4. Runs tests on BrowserStack infrastructure
5. Displays results, logs, and session recordings

**Example output**:
```json
// Browser capabilities configured
{
  "browserName": "Chrome",
  "browserVersion": "120",
  "os": "Windows",
  "osVersion": "11"
}

✓ Tests completed on 3 browsers
✓ Session recordings available
```

---

#### App Automate Test Setup
**What it does**: Sets up and runs automated mobile app tests on BrowserStack App Automate with real iOS and Android devices.

**When to use**: Testing mobile apps with Appium/XCUITest/Espresso, device matrix testing, mobile CI/CD.

**Sample commands**:
```
💬 "Upload my app to BrowserStack App Automate"
💬 "Set up Appium tests for iPhone 15 Pro and Galaxy S24"
💬 "Show me available Android devices on App Automate"
💬 "Run login.test.js on top 10 iOS and Android devices"
```

**Workflow**:
1. Uploads your .ipa or .apk file to BrowserStack
2. Lists available iOS and Android devices
3. Helps configure test framework (Appium/XCUITest/Espresso)
4. Sets device capabilities for target devices
5. Runs tests on real devices
6. Provides app logs, crash reports, and session recordings

**Example output**:
```json
// Device capabilities configured
{
  "deviceName": "iPhone 15 Pro",
  "platformName": "iOS",
  "platformVersion": "17",
  "app": "bs://abc123xyz"
}

✓ App uploaded: bs://abc123xyz
✓ Tests completed on 2 devices
✓ Video recordings available
```

---

### 🤖 AI Agent

#### Test Case Generator
**What it does**: Generates comprehensive test cases from requirements, user stories, or PRD documents using BrowserStack AI.

**When to use**: Planning new features, creating test suites, converting requirements to test cases.

**Sample commands**:
```
💬 @test-case-generator
   [Add your PRD file or requirements document to context]
   "Generate test cases for Test Management project PR-12345"

💬 @test-case-generator
   "Create test cases for a login feature with email and Google OAuth"
   "Add them to project PR-54321"
```

**Workflow**:
1. Invoke agent with `@test-case-generator`
2. Add requirements file to context (or describe feature)
3. Provide your Test Management project ID (format: `PR-12345`)
4. Agent generates structured test cases
5. Test cases are added to your BrowserStack Test Management project

**What you get**:
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

Agent: I'll generate comprehensive test cases for your login feature.

       Test cases generated:
       ✓ TC-001: Login - Valid Credentials - Success (@smoke, @p0)
       ✓ TC-002: Login - Invalid Password - Error (@regression, @p1)
       ✓ TC-003: Login - Google OAuth - Success (@smoke, @p0)
       ✓ TC-004: Login - Empty Fields - Validation (@regression, @p2)
       
       Added 4 test cases to Test Management project PR-12345
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
