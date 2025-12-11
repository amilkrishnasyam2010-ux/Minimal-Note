# New Features Added to Minimal Notes

## Overview

Two major features have been successfully added to the Minimal Notes application:

1. **Report an Issue Button** - Allow users to report problems with PDFs
2. **Light/Dark Mode Toggle** - Theme switcher for better user experience

---

## Feature 1: Report an Issue

### Description
Users can now report issues with any PDF resource directly from the viewer. This helps maintain quality and allows administrators to track problems.

### Issue Types Supported
- Wrong PDF
- Incorrect Chapter
- Broken Link
- Missing Content

### How It Works

1. **User Flow:**
   - User accesses a PDF resource
   - Clicks "Report an Issue" button below the PDF viewer
   - Selects issue type from dropdown
   - Provides detailed description
   - Submits report

2. **Data Storage:**
   - All reports are stored in `localStorage`
   - Each report includes:
     - Unique ID (UUID)
     - File key (e.g., "Maths_1")
     - Issue type
     - Description
     - Timestamp
     - Username

3. **Storage Key:**
   - `minimal-notes-issues`

### Files Created/Modified

**New Files:**
- `/src/lib/issues.ts` - Issue storage and management
- `/src/components/resource/ReportIssueDialog.tsx` - Report dialog component

**Modified Files:**
- `/src/components/resource/PdfViewer.tsx` - Added Report Issue button

### Usage Example

```typescript
import { issueStorage } from '@/lib/issues';

// Get all issues
const allIssues = issueStorage.getAll();

// Get issues for specific file
const mathsIssues = issueStorage.getByFileKey('Maths_1');

// Delete an issue
issueStorage.delete('issue-id');

// Clear all issues
issueStorage.clear();
```

### UI Location
- **Button Location:** Below the PDF preview/download buttons
- **Button Style:** Ghost variant with AlertCircle icon
- **Dialog:** Modal dialog with form

---

## Feature 2: Light/Dark Mode Toggle

### Description
Users can now switch between light mode, dark mode, and system preference. The theme preference is saved and persists across sessions.

### Theme Options
- **Light Mode** - Bright, clean interface
- **Dark Mode** - Easy on the eyes, perfect for night studying
- **System** - Automatically matches device preference

### How It Works

1. **Theme Provider:**
   - Wraps entire application
   - Manages theme state
   - Persists preference to localStorage

2. **Theme Toggle:**
   - Located in header (top-right)
   - Dropdown menu with three options
   - Animated sun/moon icon

3. **Storage Key:**
   - `minimal-notes-theme`

### Files Created/Modified

**New Files:**
- `/src/components/common/ThemeProvider.tsx` - Theme context provider
- `/src/components/common/ThemeToggle.tsx` - Theme toggle button

**Modified Files:**
- `/src/App.tsx` - Wrapped with ThemeProvider
- `/src/components/common/Header.tsx` - Added ThemeToggle button

### Usage Example

```typescript
import { useTheme } from '@/components/common/ThemeProvider';

function MyComponent() {
  const { theme, setTheme } = useTheme();
  
  // Get current theme
  console.log(theme); // 'light' | 'dark' | 'system'
  
  // Change theme
  setTheme('dark');
}
```

### UI Location
- **Toggle Location:** Header, next to user menu
- **Icon:** Sun/Moon with smooth transition
- **Dropdown:** Three options (Light, Dark, System)

---

## Technical Details

### Dependencies
No new dependencies required! All features use existing libraries:
- React
- Lucide React (icons)
- shadcn/ui components
- localStorage API

### Browser Compatibility
- All modern browsers (Chrome, Firefox, Safari, Edge)
- localStorage support required
- CSS custom properties support required

### Performance
- Minimal impact on performance
- Theme changes are instant
- Issue reports are stored locally (no network calls)

---

## Testing Instructions

### Test Report Issue Feature

1. **Login to the app**
2. **Navigate to any resource:**
   - Go to Dashboard
   - Click Notes, Questions, or One Word
   - Select a subject (e.g., Maths)
   - Select a chapter
   - Enter access code if required

3. **Report an issue:**
   - Click "Report an Issue" button
   - Select issue type (e.g., "Wrong PDF")
   - Enter description (e.g., "This PDF shows Chapter 2 content instead of Chapter 1")
   - Click "Submit Report"
   - Should see success toast notification

4. **Verify storage:**
   - Open browser DevTools (F12)
   - Go to Application/Storage tab
   - Check localStorage
   - Look for key: `minimal-notes-issues`
   - Should see your report in JSON format

### Test Dark Mode Feature

1. **Find the theme toggle:**
   - Look in the header (top-right)
   - Should see a sun/moon icon button

2. **Test Light Mode:**
   - Click theme toggle
   - Select "Light"
   - Interface should switch to light theme
   - Refresh page - theme should persist

3. **Test Dark Mode:**
   - Click theme toggle
   - Select "Dark"
   - Interface should switch to dark theme
   - Refresh page - theme should persist

4. **Test System Mode:**
   - Click theme toggle
   - Select "System"
   - Theme should match your OS preference
   - Change OS theme - app should update automatically

5. **Verify storage:**
   - Open browser DevTools (F12)
   - Go to Application/Storage tab
   - Check localStorage
   - Look for key: `minimal-notes-theme`
   - Should show: "light", "dark", or "system"

---

## Future Enhancements

### Report Issue Feature
- [ ] Admin dashboard to view all reports
- [ ] Email notifications for new reports
- [ ] Export reports to CSV
- [ ] Mark reports as resolved
- [ ] Add screenshots to reports
- [ ] Filter and search reports

### Dark Mode Feature
- [ ] Custom color themes
- [ ] Schedule theme changes (e.g., dark at night)
- [ ] Per-page theme preferences
- [ ] High contrast mode
- [ ] Color blind friendly themes

---

## API Reference

### Issue Storage API

```typescript
interface Issue {
  id: string;
  fileKey: string;
  issueType: 'wrong-pdf' | 'incorrect-chapter' | 'broken-link' | 'missing-content';
  description: string;
  timestamp: string;
  username: string;
}

// Get all issues
issueStorage.getAll(): Issue[]

// Add new issue
issueStorage.add(issue: Omit<Issue, 'id' | 'timestamp'>): Issue

// Get issues by file key
issueStorage.getByFileKey(fileKey: string): Issue[]

// Delete issue
issueStorage.delete(id: string): void

// Clear all issues
issueStorage.clear(): void

// Get issue type label
issueStorage.getIssueTypeLabel(type: Issue['issueType']): string
```

### Theme API

```typescript
type Theme = 'dark' | 'light' | 'system';

// Get current theme
const { theme } = useTheme();

// Set theme
const { setTheme } = useTheme();
setTheme('dark');
```

---

## Troubleshooting

### Issue Reports Not Saving

**Problem:** Reports disappear after page refresh

**Solution:**
1. Check if localStorage is enabled in browser
2. Check browser privacy settings
3. Try in incognito/private mode
4. Clear browser cache and try again

### Theme Not Persisting

**Problem:** Theme resets to default after refresh

**Solution:**
1. Check localStorage permissions
2. Verify `minimal-notes-theme` key exists
3. Check browser console for errors
4. Try clearing localStorage and setting theme again

### Theme Toggle Not Visible

**Problem:** Can't find theme toggle button

**Solution:**
1. Check if you're logged in (toggle shows for all users)
2. Look in header, next to user menu
3. Try refreshing the page
4. Check browser console for errors

---

## Screenshots

### Report Issue Dialog
```
┌─────────────────────────────────────────┐
│  Report an Issue                    ×   │
├─────────────────────────────────────────┤
│  Help us improve by reporting issues    │
│  with this resource: Maths_1            │
│                                         │
│  Issue Type:                            │
│  ┌─────────────────────────────────┐   │
│  │ Wrong PDF                    ▼  │   │
│  └─────────────────────────────────┘   │
│                                         │
│  Description:                           │
│  ┌─────────────────────────────────┐   │
│  │ Please describe the issue...    │   │
│  │                                 │   │
│  │                                 │   │
│  └─────────────────────────────────┘   │
│                                         │
│           [Cancel] [Submit Report]      │
└─────────────────────────────────────────┘
```

### Theme Toggle Menu
```
┌─────────────────┐
│  ☀ Light        │
│  ☾ Dark         │
│  ⚙ System       │
└─────────────────┘
```

---

## Summary

### What's New
- Report Issue button on all PDF viewers
- Light/Dark mode toggle in header
- Theme persistence across sessions
- Issue tracking in localStorage

### Benefits
- Better user experience with theme options
- Easy issue reporting for quality control
- No backend required (localStorage)
- Instant feedback with toast notifications

### Status
- All features implemented
- All tests passing
- No linting errors
- Ready for production

---

**Version:** 1.4.0  
**Date:** December 10, 2025  
**Status:** Complete

---

## Quick Start

1. **Refresh your browser** (Ctrl+Shift+R)
2. **Look for theme toggle** in header (sun/moon icon)
3. **Try switching themes** (Light/Dark/System)
4. **Open any PDF** and look for "Report an Issue" button
5. **Submit a test report** to see it in action

Enjoy the new features!
