---
name: test-case-generator
description: Generate comprehensive test cases from product requirements, user stories, or PRD documents using BrowserStack AI.
---

# Test Case Generator

You help users generate test cases from requirements using BrowserStack's AI-powered test case generation.

## When to Use

- User provides product requirements or user stories
- User uploads a PRD document
- Need to create test cases for new features

## Process

### 1. Get Requirements

Ask user to provide:
- Text description of the feature
- Or path to PRD file (PDF, image)

### 2. Generate Test Cases

Use BrowserStack AI to generate test cases:
```
"Generate test cases for [feature description]"
"Generate test cases from PRD file at [file path]"
```

### 3. Organize in Test Management

Create project structure:
```
"Create Test Management project called '[Project Name]'"
"Add folder '[Feature Name]' to project"
```

### 4. Review and Add Test Cases

The AI will generate test cases with:
- Test case title
- Steps to execute
- Expected results
- Priority level

Review and add to Test Management:
```
"Add these test cases to Test Management project"
```

## Example Workflow

**User**: "Generate test cases for a login feature with email and Google OAuth"

**Your approach**:
```
I'll generate comprehensive test cases for your login feature.

First, let me understand the requirements:
- Email/password login
- Google OAuth login
- Forgot password flow
- Any specific error scenarios?

Then I'll use BrowserStack AI to generate test cases covering:
- Happy path (successful login)
- Error cases (wrong password, unregistered email)
- OAuth flow
- Edge cases (empty fields, SQL injection attempts)

Once generated, I'll organize them in Test Management:
"Create Test Management project 'User Authentication'"
"Add test cases for email login scenarios"
"Add test cases for OAuth login scenarios"
```

## Test Case Structure

Each generated test case includes:
- **Title**: Clear description (e.g., "Login - Valid Credentials - Success")
- **Priority**: Critical/High/Medium/Low
- **Preconditions**: What needs to be set up
- **Steps**: Numbered actions to perform
- **Expected Results**: What should happen
- **Tags**: @smoke, @regression, @p0, etc.

## Tips for Better Test Cases

- Be specific about requirements
- Include edge cases and error scenarios
- Mention any integrations (third-party services)
- Specify target platforms (web, mobile, specific browsers)
- Note any compliance requirements (security, accessibility)
