---
name: accessibility-fix
description: Scan a webpage for accessibility issues, identify violations, generate code fixes, and verify the fixes work. Use when fixing WCAG compliance or accessibility bugs.
---

# Accessibility Fix Workflow

## When to Use

- User wants to fix accessibility issues on a page
- Need to ensure WCAG compliance
- Fixing specific accessibility bugs

## Steps

### 1. Run Accessibility Scan

Ask for the URL to scan:
```
"Run accessibility scan on [URL]"
```

Example: `"Run accessibility scan on localhost:3000"`

### 2. Analyze Results

Review the scan results and categorize issues:
- **Critical**: Blocks users (missing form labels, keyboard traps)
- **High**: Major barriers (poor color contrast, missing alt text)
- **Medium**: Best practices (heading hierarchy)

### 3. Fix Issues in Code

For each issue, provide specific code fix:

**Missing Alt Text:**
```html
<!-- Before -->
<img src="logo.png">

<!-- After -->
<img src="logo.png" alt="Company Logo">
```

**Poor Color Contrast:**
```css
/* Before - Contrast 2.8:1 (fails) */
color: #999;
background: #fff;

/* After - Contrast 4.6:1 (passes) */
color: #666;
background: #fff;
```

**Missing Form Label:**
```html
<!-- Before -->
<input type="email" placeholder="Email">

<!-- After -->
<label for="email">Email Address</label>
<input type="email" id="email" aria-required="true">
```

**Keyboard Navigation:**
```html
<!-- Before -->
<div onclick="handleClick()">Click me</div>

<!-- After -->
<button onclick="handleClick()">Click me</button>
```

### 4. Verify Fixes

After user implements fixes:
```
"Re-scan [URL] to verify accessibility issues are fixed"
```

### 5. Report Results

Confirm what was fixed and any remaining issues.

## Quick Reference

**Common WCAG Requirements:**
- Images need alt text
- Color contrast ≥ 4.5:1 for text
- All interactive elements keyboard accessible
- Forms have labels
- Proper heading hierarchy (h1 → h2 → h3)

## Example

**User**: "Fix accessibility issues on my login page at localhost:3000/login"

**Workflow**:
1. Scan: `"Run accessibility scan on localhost:3000/login"`
2. Identify: "Found 3 critical issues: missing form labels, poor contrast, no keyboard nav"
3. Fix: Provide code fixes for each issue
4. Verify: `"Re-scan localhost:3000/login"`
5. Confirm: "All critical issues resolved ✓"
