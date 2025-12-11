# Footer & Report Issue Button Guide

## Changes Made

### 1. Footer Added with Copyright and Contact Information

**Location:** Bottom of every page

**Content:**
- **Contact Information:** "For access codes contact: amilkrishnasyam2010@gmail.com"
- **Copyright:** "© 2025 Minimal Notes"

**Features:**
- Email is clickable (opens default email client)
- Mail icon for visual clarity
- Centered layout
- Responsive design
- Adapts to light/dark theme

---

## Where to Find the Report Issue Button

### Location: PDF Viewer Page

The **Report Issue** button appears when you view any PDF resource. Here's how to find it:

### Step-by-Step Guide:

```
1. LOGIN
   └─ Go to Minimal Notes homepage
   └─ Click "Login" button
   └─ Enter your username and password
   └─ Click "Login"

2. NAVIGATE TO DASHBOARD
   └─ After login, you'll see the Dashboard
   └─ Three main options:
      • Notes
      • Question Bank
      • One Word

3. SELECT RESOURCE TYPE
   └─ Click on any of the three options
   └─ Example: Click "Notes"

4. SELECT SUBJECT
   └─ You'll see 5 subjects:
      • Maths
      • Physics
      • Chemistry
      • Geography
      • History
   └─ Example: Click "Maths"

5. SELECT CHAPTER
   └─ You'll see chapter buttons (1-13 for Maths)
   └─ Example: Click "Chapter 1"

6. ENTER ACCESS CODE (if required)
   └─ A dialog will appear asking for access code
   └─ Enter the code (e.g., MNTWFOaH for Maths Chapter 1)
   └─ Click "Verify"
   └─ Note: Some chapters are free (no code needed)

7. PDF VIEWER PAGE
   └─ You'll now see the PDF viewer with:
      ┌─────────────────────────────────────┐
      │         Maths_1                     │
      │  Preview or download this resource  │
      ├─────────────────────────────────────┤
      │  [Preview PDF]  [Download PDF]      │
      │                                     │
      │  [⚠ Report an Issue]  ← HERE!      │
      └─────────────────────────────────────┘

8. CLICK "REPORT AN ISSUE"
   └─ A dialog will open with:
      • Issue Type dropdown
      • Description textarea
      • Submit button
```

---

## Report Issue Button Details

### Visual Appearance:
- **Icon:** Alert circle (⚠)
- **Text:** "Report an Issue"
- **Style:** Ghost button (subtle, full width)
- **Location:** Below Preview/Download buttons

### What You Can Report:
1. **Wrong PDF** - File doesn't match the chapter
2. **Incorrect Chapter** - Content is from a different chapter
3. **Broken Link** - PDF won't open or download
4. **Missing Content** - Pages or sections are missing

### How to Use:
1. Click "Report an Issue" button
2. Select issue type from dropdown
3. Enter detailed description
4. Click "Submit Report"
5. You'll see a success notification
6. Report is saved to localStorage

---

## Visual Layout

```
┌──────────────────────────────────────────────────────────────┐
│                        HEADER                                │
│  [Logo] Minimal Notes        [Theme] [Dashboard] [User]     │
└──────────────────────────────────────────────────────────────┘
│                                                              │
│                        MAIN CONTENT                          │
│                                                              │
│  When viewing a PDF:                                         │
│  ┌────────────────────────────────────────────────────┐     │
│  │              Maths_1                               │     │
│  │     Preview or download this resource              │     │
│  ├────────────────────────────────────────────────────┤     │
│  │  ┌──────────────┐  ┌──────────────┐              │     │
│  │  │ Preview PDF  │  │ Download PDF │              │     │
│  │  └──────────────┘  └──────────────┘              │     │
│  │                                                    │     │
│  │  ┌──────────────────────────────────────────┐    │     │
│  │  │  ⚠ Report an Issue                       │    │     │
│  │  └──────────────────────────────────────────┘    │     │
│  └────────────────────────────────────────────────────┘     │
│                                                              │
└──────────────────────────────────────────────────────────────┘
│                        FOOTER                                │
│  📧 For access codes contact:                               │
│     amilkrishnasyam2010@gmail.com                           │
│                                                              │
│  © 2025 Minimal Notes                                       │
└──────────────────────────────────────────────────────────────┘
```

---

## Quick Access Examples

### Example 1: Report Issue for Maths Chapter 1

```
1. Login
2. Dashboard → Notes
3. Select "Maths"
4. Select "Chapter 1"
5. Enter code: MNTWFOaH
6. Click "Verify"
7. Click "Report an Issue" (below PDF buttons)
8. Select issue type
9. Enter description
10. Submit
```

### Example 2: Report Issue for Free Question Bank

```
1. Login
2. Dashboard → Question Bank
3. Select "Maths"
4. Select "Chapter 6" (FREE - no code needed)
5. Click "Report an Issue" (below PDF buttons)
6. Select issue type
7. Enter description
8. Submit
```

---

## Footer Information

### Contact for Access Codes

**Email:** amilkrishnasyam2010@gmail.com

**How to Use:**
1. Click the email address in the footer
2. Your default email client will open
3. Send an email requesting access codes
4. Specify which subjects/chapters you need

**What to Include in Email:**
- Your name
- Which subjects you need (Maths, Physics, Chemistry, Geography, History)
- Which chapters you need
- Any specific requirements

### Copyright

**Text:** © 2025 Minimal Notes

**Location:** Bottom center of every page

---

## Testing Instructions

### Test Footer:

1. **Refresh browser** (Ctrl+Shift+R)
2. **Scroll to bottom** of any page
3. **Check footer displays:**
   - Email contact information
   - Copyright notice
4. **Click email link** - should open email client
5. **Test on different pages:**
   - Homepage
   - Dashboard
   - Notes page
   - Questions page
   - One Word page

### Test Report Issue Button:

1. **Login to app**
2. **Navigate to any PDF:**
   - Dashboard → Notes → Maths → Chapter 1
   - Enter code: MNTWFOaH
3. **Look for button** below Preview/Download buttons
4. **Click "Report an Issue"**
5. **Fill out form:**
   - Select "Wrong PDF"
   - Enter: "Test report - checking functionality"
6. **Submit report**
7. **Verify success notification**

---

## Files Modified

### New/Updated Files:

1. **src/components/common/Footer.tsx**
   - Added copyright notice
   - Added contact email
   - Simplified layout
   - Added mail icon

2. **src/App.tsx**
   - Imported Footer component
   - Added Footer to layout

### Existing Files (Report Issue):

1. **src/components/resource/PdfViewer.tsx**
   - Contains Report Issue button
   - Located below Preview/Download buttons

2. **src/components/resource/ReportIssueDialog.tsx**
   - Dialog component for reporting issues
   - Form with issue type and description

3. **src/lib/issues.ts**
   - Issue storage management
   - localStorage operations

---

## Troubleshooting

### Footer Not Showing

**Problem:** Can't see footer at bottom of page

**Solution:**
1. Refresh browser (Ctrl+Shift+R)
2. Scroll to bottom of page
3. Check browser console for errors (F12)
4. Clear browser cache

### Report Issue Button Not Visible

**Problem:** Can't find Report Issue button

**Solution:**
1. Make sure you're viewing a PDF resource
2. Look below the Preview/Download buttons
3. Scroll down if needed
4. Refresh page (Ctrl+Shift+R)
5. Try a different resource

### Email Link Not Working

**Problem:** Clicking email doesn't open email client

**Solution:**
1. Check if you have a default email client set
2. Copy email manually: amilkrishnasyam2010@gmail.com
3. Use webmail (Gmail, Outlook, etc.)
4. Try different browser

---

## Summary

### What's New:

✅ **Footer Added**
- Copyright: © 2025 Minimal Notes
- Contact: amilkrishnasyam2010@gmail.com
- Visible on all pages
- Clickable email link

✅ **Report Issue Button Location**
- On PDF viewer page
- Below Preview/Download buttons
- Available for all resources
- Easy to find and use

### Status:

- All changes implemented
- Lint check passed
- No errors
- Ready to use

---

**Version:** 1.4.2
**Date:** December 10, 2025
**Status:** Complete

---

## Quick Reference

### Footer Location:
```
Bottom of every page
```

### Report Issue Button Location:
```
PDF Viewer Page → Below Preview/Download buttons
```

### Contact Email:
```
amilkrishnasyam2010@gmail.com
```

### Copyright:
```
© 2025 Minimal Notes
```

---

**Refresh your browser now to see the changes!**

Press: Ctrl+Shift+R (Windows/Linux) or Cmd+Shift+R (Mac)
