# How to Make Resources Free (No Access Code Required)

## 📝 Quick Guide

To make any resource free (no access code required), you simply need to add it to the `FREE_RESOURCES` array in `script.js`.

---

## 🔧 Step-by-Step Instructions

### Step 1: Open script.js

Extract your `Minimal-Notes.zip` and open the `script.js` file in a text editor.

### Step 2: Find the FREE_RESOURCES Array

Look for this section near the top of the file (around line 14):

```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];
```

### Step 3: Add Your Resource

Add the file key of the resource you want to make free to this array.

**File Key Format:**
- Notes: `Subject_Chapter` (e.g., `Maths_1`)
- Question Bank: `Subject_Chapter_QB` (e.g., `Maths_1_QB`)
- One Word: `Subject_Chapter_OW` (e.g., `Maths_1_OW`)

### Step 4: Save the File

Save `script.js` after making your changes.

---

## 📋 Examples

### Example 1: Make Maths Chapter 1 Notes Free

**Before:**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];
```

**After:**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB', 'Maths_1'];
```

### Example 2: Make Chemistry Chapter 3 Question Bank Free

**Before:**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];
```

**After:**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB', 'Chemistry_3_QB'];
```

### Example 3: Make Multiple Resources Free

**Before:**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];
```

**After:**
```javascript
const FREE_RESOURCES = [
  'Maths_6_QB', 
  'Maths_7_QB', 
  'Physics_5_QB', 
  'History_4_QB',
  'Maths_1',           // Maths Chapter 1 Notes
  'Maths_1_QB',        // Maths Chapter 1 Question Bank
  'Maths_1_OW',        // Maths Chapter 1 One Word
  'Physics_1',         // Physics Chapter 1 Notes
  'Chemistry_3_QB'     // Chemistry Chapter 3 Question Bank
];
```

### Example 4: Make All Maths Chapters Free

```javascript
const FREE_RESOURCES = [
  'Maths_6_QB', 
  'Maths_7_QB', 
  'Physics_5_QB', 
  'History_4_QB',
  // All Maths Notes
  'Maths_1', 'Maths_2', 'Maths_3', 'Maths_4', 'Maths_5', 
  'Maths_6', 'Maths_7', 'Maths_8', 'Maths_9', 'Maths_10',
  'Maths_11', 'Maths_12', 'Maths_13',
  // All Maths Question Banks
  'Maths_1_QB', 'Maths_2_QB', 'Maths_3_QB', 'Maths_4_QB', 'Maths_5_QB',
  'Maths_8_QB', 'Maths_9_QB', 'Maths_10_QB', 'Maths_11_QB', 'Maths_12_QB', 'Maths_13_QB',
  // All Maths One Word
  'Maths_1_OW', 'Maths_2_OW', 'Maths_3_OW', 'Maths_4_OW', 'Maths_5_OW',
  'Maths_6_OW', 'Maths_7_OW', 'Maths_8_OW', 'Maths_9_OW', 'Maths_10_OW',
  'Maths_11_OW', 'Maths_12_OW', 'Maths_13_OW'
];
```

---

## 📚 File Key Reference

### Maths (Chapters 1-13)
```
Notes:         Maths_1, Maths_2, ..., Maths_13
Question Bank: Maths_1_QB, Maths_2_QB, ..., Maths_13_QB
One Word:      Maths_1_OW, Maths_2_OW, ..., Maths_13_OW
```

### Physics (Chapters 1-7)
```
Notes:         Physics_1, Physics_2, ..., Physics_7
Question Bank: Physics_1_QB, Physics_2_QB, ..., Physics_7_QB
One Word:      Physics_1_OW, Physics_2_OW, ..., Physics_7_OW
```

### Chemistry (Chapters 1-7)
```
Notes:         Chemistry_1, Chemistry_2, ..., Chemistry_7
Question Bank: Chemistry_1_QB, Chemistry_2_QB, ..., Chemistry_7_QB
One Word:      Chemistry_1_OW, Chemistry_2_OW, ..., Chemistry_7_OW
```

### Biology (Chapters 1-6)
```
Notes:         Biology_1, Biology_2, ..., Biology_6
Question Bank: Biology_1_QB, Biology_2_QB, ..., Biology_6_QB
One Word:      Biology_1_OW, Biology_2_OW, ..., Biology_6_OW
```

### Geography (Chapters 1-8)
```
Notes:         Geography_1, Geography_2, ..., Geography_8
Question Bank: Geography_1_QB, Geography_2_QB, ..., Geography_8_QB
One Word:      Geography_1_OW, Geography_2_OW, ..., Geography_8_OW
```

### History (Chapters 1-9)
```
Notes:         History_1, History_2, ..., History_9
Question Bank: History_1_QB, History_2_QB, ..., History_9_QB
One Word:      History_1_OW, History_2_OW, ..., History_9_OW
```

---

## 🧪 Testing Your Changes

### 1. Save and Test Locally

```bash
# Navigate to your Minimal-Notes directory
cd Minimal-Notes

# Start local server
python -m http.server 8000

# Open browser
# http://localhost:8000
```

### 2. Test the Free Resource

1. Login or create an account
2. Navigate to the resource you made free
3. Select the subject and chapter
4. **Expected behavior**: 
   - No access code prompt should appear
   - PDF should open directly
   - Or you should see a "FREE" indicator

### 3. Verify in Console

Open browser console (F12) and you should see:
```
Resource Maths_1 is free - no access code required
```

---

## 💡 Tips

### Tip 1: Use Comments for Organization

```javascript
const FREE_RESOURCES = [
  // Original free resources
  'Maths_6_QB', 
  'Maths_7_QB', 
  'Physics_5_QB', 
  'History_4_QB',
  
  // Promotional free resources
  'Maths_1',
  'Physics_1',
  
  // Free trial chapters
  'Chemistry_1_QB',
  'Biology_1_QB'
];
```

### Tip 2: Keep Track of Free Resources

Create a separate document listing all free resources for easy reference:

```
FREE RESOURCES LIST
===================
Maths_6_QB      - Original
Maths_7_QB      - Original
Physics_5_QB    - Original
History_4_QB    - Original
Maths_1         - Added Dec 10, 2025
Physics_1       - Added Dec 10, 2025
```

### Tip 3: Validate File Keys

Make sure the file key exactly matches the PDF filename:
- ✅ Correct: `Maths_1` (matches `Maths_1.pdf`)
- ❌ Wrong: `maths_1` (lowercase)
- ❌ Wrong: `Maths 1` (space instead of underscore)
- ❌ Wrong: `Maths_01` (leading zero)

---

## 🔄 Reverting Changes

To make a resource require an access code again, simply remove it from the `FREE_RESOURCES` array.

**Before (Free):**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB', 'Maths_1'];
```

**After (Requires Code):**
```javascript
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];
```

---

## 📍 Exact Location in script.js

The `FREE_RESOURCES` array is located at:
- **File**: `script.js`
- **Line**: ~14 (near the top, after SUBJECTS array)
- **Section**: Configuration

```javascript
// ============================================
// CONFIGURATION
// ============================================

const SUBJECTS = [
  { id: 'Maths', name: 'Maths', chapters: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13] },
  { id: 'Physics', name: 'Physics', chapters: [1, 2, 3, 4, 5, 6, 7] },
  { id: 'Chemistry', name: 'Chemistry', chapters: [1, 2, 3, 4, 5, 6, 7] },
  { id: 'Biology', name: 'Biology', chapters: [1, 2, 3, 4, 5, 6] },
  { id: 'Geography', name: 'Geography', chapters: [1, 2, 3, 4, 5, 6, 7, 8] },
  { id: 'History', name: 'History', chapters: [1, 2, 3, 4, 5, 6, 7, 8, 9] }
];

const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];  // ← EDIT THIS LINE

const RESOURCE_TYPES = {
  notes: { suffix: '', name: 'Notes' },
  questions: { suffix: '_QB', name: 'Question Bank' },
  oneword: { suffix: '_OW', name: 'One Word' }
};
```

---

## ⚠️ Important Notes

### 1. Case Sensitive
File keys are **case sensitive**. Use exact capitalization:
- ✅ `Maths_1`
- ❌ `maths_1`

### 2. Underscore Required
Use underscore `_` not space or hyphen:
- ✅ `Maths_1`
- ❌ `Maths 1`
- ❌ `Maths-1`

### 3. No File Extension
Don't include `.pdf` in the file key:
- ✅ `Maths_1`
- ❌ `Maths_1.pdf`

### 4. Exact Match
The file key must exactly match the PDF filename (without extension):
- PDF file: `Maths_1.pdf`
- File key: `Maths_1` ✅

---

## 🎯 Common Use Cases

### Use Case 1: Free Trial
Make first chapter of each subject free:

```javascript
const FREE_RESOURCES = [
  'Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB',
  'Maths_1', 'Physics_1', 'Chemistry_1', 'Biology_1', 'Geography_1', 'History_1'
];
```

### Use Case 2: Free Question Banks
Make all question banks free, but keep notes and one word paid:

```javascript
const FREE_RESOURCES = [
  // Maths QB
  'Maths_1_QB', 'Maths_2_QB', 'Maths_3_QB', 'Maths_4_QB', 'Maths_5_QB',
  'Maths_6_QB', 'Maths_7_QB', 'Maths_8_QB', 'Maths_9_QB', 'Maths_10_QB',
  'Maths_11_QB', 'Maths_12_QB', 'Maths_13_QB',
  // Physics QB
  'Physics_1_QB', 'Physics_2_QB', 'Physics_3_QB', 'Physics_4_QB', 
  'Physics_5_QB', 'Physics_6_QB', 'Physics_7_QB',
  // Add more as needed...
];
```

### Use Case 3: Promotional Period
Make specific chapters free for a limited time:

```javascript
const FREE_RESOURCES = [
  'Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB',
  // Promotional - December 2025
  'Maths_8', 'Maths_8_QB', 'Maths_8_OW',
  'Physics_3', 'Physics_3_QB', 'Physics_3_OW'
];
```

---

## 🚀 Quick Reference

### Make a Single Resource Free
1. Open `script.js`
2. Find line 14: `const FREE_RESOURCES = [...]`
3. Add your file key: `'Subject_Chapter'` or `'Subject_Chapter_QB'` or `'Subject_Chapter_OW'`
4. Save file
5. Test locally
6. Deploy

### Example: Make Maths Chapter 8 Notes Free
```javascript
// Before
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB'];

// After
const FREE_RESOURCES = ['Maths_6_QB', 'Maths_7_QB', 'Physics_5_QB', 'History_4_QB', 'Maths_8'];
```

---

## ✅ Checklist

Before deploying your changes:

- [ ] Opened `script.js`
- [ ] Found `FREE_RESOURCES` array (line ~14)
- [ ] Added file key(s) in correct format
- [ ] Used correct capitalization
- [ ] Used underscore (not space or hyphen)
- [ ] Did not include `.pdf` extension
- [ ] Saved file
- [ ] Tested locally
- [ ] Verified resource is free (no access code prompt)
- [ ] Checked browser console for confirmation
- [ ] Ready to deploy

---

## 📞 Need Help?

### Check These Files
- `script.js` - Main configuration file
- `COMPLETE_ACCESS_CODES.txt` - List of all file keys
- `README.md` - General documentation

### Common Issues

**Issue**: Resource still asks for access code  
**Solution**: Check file key spelling and capitalization

**Issue**: "Resource not found" error  
**Solution**: Verify PDF file exists with exact same name

**Issue**: Changes not working  
**Solution**: Clear browser cache and reload page

---

**That's it! Making resources free is as simple as adding them to the FREE_RESOURCES array!** 🎉

---

*Last Updated: December 10, 2025*  
*Version: 1.2.0*
