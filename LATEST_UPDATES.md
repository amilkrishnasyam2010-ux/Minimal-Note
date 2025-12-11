# Minimal Notes - Latest Updates

## Recent Changes Summary

### 1. Footer Updates
**Added to bottom of every page:**
- 📖 "Based on Kerala SCERT 10th standard syllabus"
- 📧 Contact email: amilkrishnasyam2010@gmail.com (clickable)
- © 2025 Minimal Notes

**Location:** `src/components/common/Footer.tsx`

---

### 2. Theme Toggle (Light/Dark Mode)
**Features:**
- Sun/Moon icon button in header
- Three modes: Light, Dark, System
- Persists preference to localStorage
- Smooth transitions

**Files:**
- `src/components/common/ThemeProvider.tsx`
- `src/components/common/ThemeToggle.tsx`
- Updated: `src/App.tsx`

---

### 3. Report Issue Button
**Location:** PDF viewer page (below Preview/Download buttons)

**Features:**
- Report 4 types of issues: Wrong PDF, Incorrect Chapter, Broken Link, Missing Content
- Stores reports in localStorage
- Toast notifications

**Files:**
- `src/components/resource/ReportIssueDialog.tsx`
- `src/lib/issues.ts`
- Updated: `src/components/resource/PdfViewer.tsx`

**How to find it:**
1. Login → Dashboard
2. Select Notes/Questions/One Word
3. Choose subject and chapter
4. Enter access code
5. Look below PDF buttons

---

### 4. Netlify Deployment Fix
**Problem:** pnpm lockfile out of sync with package.json

**Solution Applied:**
- Updated `miaoda-auth-react`: `2.0.6` → `^2.0.6`
- Updated `miaoda-sc-plugin`: `1.0.29` → `^1.0.31`
- Used pnpm 10.24.0 (matches Netlify CI)
- Committed changes to git

**Status:** ✅ Ready to deploy (push to trigger Netlify build)

---

## Quick Reference

### Footer Content (Top to Bottom):
1. Syllabus: "Based on Kerala SCERT 10th standard syllabus"
2. Contact: "For access codes contact: amilkrishnasyam2010@gmail.com"
3. Copyright: "© 2025 Minimal Notes"

### Theme Toggle:
- Location: Header (sun/moon icon)
- Storage: localStorage key "minimal-notes-theme"

### Report Issue:
- Location: PDF viewer page
- Storage: localStorage key "minimal-notes-issues"

---

## Verification Status

✅ All features implemented
✅ Lint check passed (89 files, 0 errors)
✅ No breaking changes
✅ Ready for deployment

---

## Next Steps

1. **Refresh browser** to see changes:
   - Press: Ctrl+Shift+R (Windows/Linux)
   - Press: Cmd+Shift+R (Mac)

2. **Push to deploy** (fixes Netlify error):
   ```bash
   git push origin master
   ```

3. **Test features:**
   - Check footer on any page
   - Try theme toggle in header
   - Test report issue on PDF viewer

---

**Version:** 1.4.4
**Date:** December 10, 2025
**Status:** Complete and Ready to Deploy
