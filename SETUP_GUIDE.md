# Minimal Notes - Setup Guide

Welcome to Minimal Notes! This guide will help you set up and deploy your educational resource platform.

## 🎯 What You Have

A complete, frontend-only web application with:
- ✅ Superlist-inspired modern design
- ✅ User authentication (localStorage-based)
- ✅ 5 subjects: Maths, Physics, Chemistry, Biology, Social Science
- ✅ 3 resource types: Notes, Question Bank, One Word
- ✅ Access code system with free resources
- ✅ Download tracking
- ✅ Fully responsive design
- ✅ No backend required

## 📋 Quick Setup Checklist

### 1. Add Your Logo
- [ ] Place your logo image at `public/images/logo.png`
- [ ] Recommended size: 32x32px or 64x64px
- [ ] Format: PNG with transparent background

### 2. Add PDF Files
- [ ] Navigate to `public/pdfs/` directory
- [ ] Add your PDF files following the naming convention (see below)
- [ ] Verify file names match exactly (case-sensitive)

### 3. Test Locally
- [ ] Run `npm install` to install dependencies
- [ ] Run `npm run dev` to start development server
- [ ] Open `http://localhost:5173` in your browser
- [ ] Create a test account and verify functionality

### 4. Deploy
- [ ] Follow the deployment guide in `DEPLOYMENT.md`
- [ ] Deploy to GitHub Pages, Netlify, or Vercel
- [ ] Test the deployed version

## 📁 PDF File Naming Convention

### Format Rules

**Notes:**
```
{Subject}_{Chapter}.pdf
```
Examples: `Maths_1.pdf`, `Chemistry_3.pdf`, `Biology_5.pdf`

**Question Banks:**
```
{Subject}_{Chapter}_QB.pdf
```
Examples: `Maths_6_QB.pdf`, `Physics_5_QB.pdf`, `Social Science_8_QB.pdf`

**One Word:**
```
{Subject}_{Chapter}_OW.pdf
```
Examples: `Maths_1_OW.pdf`, `Chemistry_2_OW.pdf`, `Biology_4_OW.pdf`

### Subject Names (Use Exact Spelling)

- `Maths` (Chapters 1-7)
- `Physics` (Chapters 1-7)
- `Chemistry` (Chapters 1-7)
- `Biology` (Chapters 1-6)
- `Social Science` (Chapters 1-9) - **Note the space!**

### Your Current PDFs

Based on your requirements, you mentioned these PDFs:

**Notes:**
- ✅ Chemistry_3.pdf
- ✅ Geography_3.pdf (Note: Geography is not in the subject list, consider renaming to Social Science_3.pdf)
- ✅ History_3.pdf (Note: History is not in the subject list, consider renaming to Social Science_3.pdf)

**Question Banks:**
- ✅ History_4_QB.pdf (FREE) - Consider renaming to Social Science_4_QB.pdf
- ✅ Maths_6_QB.pdf (FREE)
- ✅ Maths_7_QB.pdf (FREE)
- ✅ Physics_5_QB.pdf (FREE)

## 🆓 Free Resources

These resources don't require an access code:
- Maths Chapter 6 - Question Bank
- Maths Chapter 7 - Question Bank
- Physics Chapter 5 - Question Bank
- History Chapter 4 - Question Bank (if you rename it to Social Science_4_QB.pdf, update the free resources list)

## 🔑 Access Codes

Access codes are automatically generated. Users will see them in the console when they try to access a resource.

To find an access code:
1. Open browser developer tools (F12)
2. Go to Console tab
3. Try to access a resource
4. The expected code will be printed in the console

Or refer to `ACCESS_CODES.md` for a complete list.

## 🎨 Customization

### Change Colors

Edit `src/index.css` to customize the color scheme:

```css
:root {
  --primary: 217 91% 60%;  /* Main blue color */
  --secondary: 210 40% 96%; /* Light gray */
  /* ... other colors */
}
```

### Change Logo

Replace `public/images/logo.png` with your own logo.

### Add More Subjects

Edit `src/lib/accessCode.ts`:

```typescript
export const subjects = [
  { id: 'Maths', name: 'Maths', chapters: [1, 2, 3, 4, 5, 6, 7] },
  // Add more subjects here
];
```

## 🚀 Deployment Options

### Option 1: GitHub Pages (Recommended)

1. Push your code to GitHub
2. Go to repository Settings → Pages
3. Select "GitHub Actions" as source
4. The site will deploy automatically

### Option 2: Netlify

1. Connect your GitHub repository to Netlify
2. Build command: `npm run build`
3. Publish directory: `dist`
4. Deploy!

### Option 3: Vercel

1. Import your GitHub repository to Vercel
2. Framework preset: Vite
3. Deploy!

## 🧪 Testing

### Test User Authentication

1. Click "Sign Up" and create an account
2. Log out
3. Log in with the same credentials
4. Verify you're redirected to the dashboard

### Test Resource Access

1. Go to Dashboard
2. Click "Notes", "Question Bank", or "One Word"
3. Select a subject
4. Select a chapter
5. For free resources: Should show PDF immediately
6. For paid resources: Should ask for access code

### Test Download Tracking

1. Download a PDF
2. Go back to Dashboard
3. Verify the download appears in "Your Downloads"

## 📝 Important Notes

### File Names Are Case-Sensitive

- ✅ Correct: `Maths_1.pdf`
- ❌ Wrong: `maths_1.pdf`, `MATHS_1.pdf`

### Subject Names Must Match Exactly

- ✅ Correct: `Social Science_5.pdf` (with space)
- ❌ Wrong: `SocialScience_5.pdf`, `social science_5.pdf`

### PDF Files Must Be in public/pdfs/

- ✅ Correct: `public/pdfs/Maths_1.pdf`
- ❌ Wrong: `src/pdfs/Maths_1.pdf`, `pdfs/Maths_1.pdf`

## 🆘 Troubleshooting

### PDF Not Loading

1. Check file name matches exactly (case-sensitive)
2. Verify file is in `public/pdfs/` directory
3. Check browser console for errors
4. Try accessing the PDF directly: `http://localhost:5173/pdfs/Maths_1.pdf`

### Access Code Not Working

1. Check the console for the expected code
2. Verify you're entering the code exactly (case-sensitive)
3. Make sure the resource isn't in the free list

### Login Not Working

1. Clear browser localStorage: `localStorage.clear()` in console
2. Try creating a new account
3. Check browser console for errors

### Deployment Issues

1. Verify `base` in `vite.config.ts` matches your repository name
2. Check that all files are committed and pushed
3. Verify build completes successfully: `npm run build`

## 📚 Additional Resources

- [User Guide](./USER_GUIDE.md) - Guide for end users
- [Deployment Guide](./DEPLOYMENT.md) - Detailed deployment instructions
- [Access Codes Reference](./ACCESS_CODES.md) - Complete list of access codes
- [PDF Files Guide](./public/pdfs/README.md) - PDF naming conventions

## 🎉 You're Ready!

Your Minimal Notes application is ready to use. Follow the checklist above to complete the setup, and refer to the documentation for detailed information.

If you encounter any issues, check the troubleshooting section or review the relevant documentation.

Happy learning! 📖
