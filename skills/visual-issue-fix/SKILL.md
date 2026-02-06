---
name: visual-issue-fix
description: Capture screenshots of a page across browsers, identify visual issues, fix them in code, and validate. Use for cross-browser layout bugs or visual regressions.
---

# Visual Issue Fix Workflow

## When to Use

- Layout broken in specific browser
- Visual bugs reported by users
- Cross-browser design inconsistencies
- Responsive design issues

## Steps

### 1. Capture Screenshots

Open page on target browsers:
```
"Open [URL] on Chrome"
"Open [URL] on Safari"
"Open [URL] on Firefox"
```

Take screenshots:
```
"Take screenshot of the current page"
```

### 2. Identify Issues

Compare screenshots and identify:
- Layout differences (alignment, spacing)
- Missing elements
- Broken styling (fonts, colors, borders)
- Responsive breakpoint problems

### 3. Fix in Code

Provide specific code fixes:

**Flexbox Issue:**
```css
/* Before - Safari issue */
.container {
  display: flex;
  gap: 20px;
}

/* After - Works everywhere */
.container {
  display: flex;
}
.container > * {
  margin-right: 20px;
}
```

**CSS Grid Issue:**
```css
/* Before - IE11 doesn't support */
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

/* After - Fallback for old browsers */
.grid {
  display: flex;
  flex-wrap: wrap;
}
@supports (display: grid) {
  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
}
```

**Responsive Issue:**
```css
/* Before - Fixed width breaks on mobile */
.sidebar {
  width: 300px;
}

/* After - Responsive */
.sidebar {
  width: 100%;
}
@media (min-width: 768px) {
  .sidebar {
    width: 300px;
  }
}
```

### 4. Validate Fix

After user implements fix:
```
"Re-open [URL] on [browser] to verify the fix"
"Take screenshot to confirm layout is correct"
```

### 5. Test Other Browsers

Ensure fix didn't break other browsers:
```
"Test on Chrome, Firefox, Safari, and Edge"
```

## Quick Tips

- Test on real devices, not just dev tools
- Check both desktop and mobile
- Verify at different screen sizes
- Look for vendor prefix needs (-webkit-, -moz-)

## Example

**User**: "My navigation is broken in Safari"

**Workflow**:
1. Capture: `"Open localhost:3000 on Safari"` + `"Take screenshot"`
2. Identify: "Navigation items overlapping - flexbox gap issue"
3. Fix: Provide CSS fix replacing gap with margins
4. Validate: `"Re-open localhost:3000 on Safari"` - confirm fixed
5. Cross-check: Test on Chrome, Firefox to ensure no regression
