---
name: test-case-generator
description: Generate comprehensive test cases from product requirements using uploadProductRequirementFile and createTestCasesFromFile MCP tools. Use when converting requirements to test cases.
---

# Test Case Generator

You help users generate test cases from requirements using BrowserStack's AI-powered test case generation.

## MCP Tools Used

- `uploadProductRequirementFile` (Tool #20) - Upload PRD/PDF/screenshot files
- `createTestCasesFromFile` (Tool #8) - Generate test cases from uploaded files

## When to Use

- User provides product requirements or user stories
- User uploads a PRD document
- Need to create test cases for new features

## Process

### 1. Upload Requirements File

Use `uploadProductRequirementFile` to upload the PRD:

```
"Upload PRD from /Users/xyz/Desktop/login-flow.pdf and use BrowserStack AI to generate test cases"
```

**What the tool does:**
- Uploads PDF, screenshot, or requirements document
- Returns a file mapping ID for use in test case generation
- Prepares file for AI processing

### 2. Generate Test Cases

Use `createTestCasesFromFile` to generate test cases from the uploaded file:

```
"Upload test cases from '/Users/xyz/testcases.pdf' to the 'Shopping App' project in Test Management"
"Generate test cases for project PR-12345 from the uploaded requirements"
```

**What the tool does:**
- Analyzes uploaded requirements using AI
- Generates comprehensive test cases
- Automatically adds them to specified Test Management project
- Includes title, steps, expected results, priority, and tags

### 3. Specify Test Management Project

Provide the project identifier (format: `PR-xxxxx`):

```
"Add generated test cases to Test Management project PR-12345"
```

## Example Workflow

**User**: "@test-case-generator Generate test cases for project PR-12345"
[User attaches: login-feature-spec.pdf]

**Your approach**:
1. Upload file: Use `uploadProductRequirementFile` with the attached PDF
2. Generate: Use `createTestCasesFromFile` to create test cases for project PR-12345
3. Confirm: Report which test cases were generated and added

**Response**:
```
✓ PRD uploaded and analyzed
✓ Generated 6 test cases for login feature:

Test cases added to project PR-12345:
- TC-001: Login - Valid Credentials - Success (@smoke, @p0)
- TC-002: Login - Invalid Password - Error (@regression, @p1)
- TC-003: Login - Unregistered Email - Error (@regression, @p1)
- TC-004: Login - Google OAuth - Success (@smoke, @p0)
- TC-005: Login - Empty Fields - Validation (@regression, @p2)
- TC-006: Login - SQL Injection Prevention (@security, @p1)

All test cases added to Test Management project PR-12345
```

## Test Case Structure

Each generated test case includes:
- **Title**: Clear description (e.g., "Login - Valid Credentials - Success")
- **Priority**: Critical/High/Medium/Low
- **Preconditions**: What needs to be set up
- **Steps**: Numbered actions to perform
- **Expected Results**: What should happen
- **Tags**: @smoke, @regression, @p0, @security, etc.

## Required Information

To generate test cases, you need:
1. **Requirements file**: PRD, PDF, or screenshot (uploaded via `uploadProductRequirementFile`)
2. **Project ID**: Test Management project identifier (format: `PR-xxxxx`)

## Tips for Better Test Cases

- Ensure requirements file is detailed and clear
- Include edge cases and error scenarios in requirements
- Mention any integrations (third-party services)
- Specify target platforms (web, mobile, specific browsers)
- Note any compliance requirements (security, accessibility)
