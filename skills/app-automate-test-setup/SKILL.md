---
name: app-automate-test-setup
description: Set up and run automated mobile app tests on BrowserStack App Automate. Use for testing iOS/Android apps with Appium, XCUITest, or Espresso on real devices.
---

# App Automate Test Setup Workflow

## When to Use

- Testing mobile apps on real iOS and Android devices
- Running Appium tests across device matrix
- CI/CD integration for mobile app testing
- Device-specific bug reproduction

## Steps

### 1. Upload Your App

Upload your .apk (Android) or .ipa (iOS) file:
```
"Upload my app to BrowserStack App Automate"
```

Or provide app URL:
```
"Use app at https://example.com/app.apk"
```

### 2. Get Available Devices

List all devices and OS versions:
```
"Show me available iOS devices on App Automate"
"Show me available Android devices on App Automate"
```

### 3. Configure Test

Choose your test framework:

**For Appium (Java/Python/Node.js/Ruby):**
```
"Help me set up Appium tests for BrowserStack App Automate"
```

**For XCUITest (iOS native):**
```
"Configure XCUITest to run on BrowserStack"
```

**For Espresso (Android native):**
```
"Set up Espresso tests for BrowserStack"
```

### 4. Set Device Capabilities

Specify which devices to test on:
```
"I want to test on iPhone 15 Pro (iOS 17) and Samsung Galaxy S23 (Android 14)"
```

The agent will help configure capabilities like:
```json
{
  "deviceName": "iPhone 15 Pro",
  "platformName": "iOS",
  "platformVersion": "17",
  "app": "bs://app-id"
}
```

### 5. Run Tests

Execute your test suite:
```
"Run my app tests on BrowserStack App Automate"
```

Or run specific tests:
```
"Run login.test.js on iPhone 15 and Galaxy S23"
```

### 6. View Results

Check test execution results:
```
"Show me the latest App Automate test results"
"Get the session recording for the last test run"
```

## Common Scenarios

**Device Matrix Testing:**
```
"Run tests on top 10 iOS devices and top 10 Android devices"
```

**Debugging Failed Tests:**
```
"Show me app logs and device logs for the failed test"
"Get screenshots and video from the test session"
```

**Testing Different OS Versions:**
```
"Test on iOS 16, 17, and 18"
"Test on Android 12, 13, and 14"
```

**Network Simulation:**
```
"Run tests with 3G network speed"
"Test under airplane mode conditions"
```

## Example

**User**: "I need to test my login feature on latest iPhone and Samsung phones"

**Workflow**:
1. Upload app: `"Upload MyApp.ipa to BrowserStack"`
2. Get devices: `"Show latest iPhone and Samsung devices"`
3. Configure: `"Set up Appium tests for iPhone 15 Pro and Galaxy S24"`
4. Run: `"Run login.test.js on both devices"`
5. Results: `"Show test results and any crashes"`
6. Debug: If failures → `"Get app logs and crash reports"`

## Quick Tips

- Upload apps once, reuse the app_url across tests
- Test on devices matching your user base
- Use network throttling to test under poor conditions
- Enable video recording for visual debugging
- Check device logs for native crashes
- Test different device orientations (portrait/landscape)
