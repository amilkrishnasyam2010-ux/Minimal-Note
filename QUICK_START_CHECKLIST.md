# Quick Start Checklist

Use this checklist to get your Minimal Notes application up and running quickly.

## ✅ Pre-Deployment Checklist

### 1. Logo (Optional)
- [ ] Add your logo as `public/images/logo.png` (32x32 or 64x64 recommended)
- [ ] Or keep the placeholder SVG logo (already included)

### 2. PDF Files (Required)
- [ ] Navigate to `public/pdfs/` directory
- [ ] Add your PDF files following the naming convention:
  - Notes: `{Subject}_{Chapter}.pdf`
  - Question Bank: `{Subject}_{Chapter}_QB.pdf`
  - One Word: `{Subject}_{Chapter}_OW.pdf`

#### Your Mentioned PDFs:
- [ ] Chemistry_3.pdf
- [ ] Geography_3.pdf (or rename to Social Science_3.pdf)
- [ ] History_3.pdf (or rename to Social Science_3.pdf)
- [ ] History_4_QB.pdf (FREE - or rename to Social Science_4_QB.pdf)
- [ ] Maths_6_QB.pdf (FREE)
- [ ] Maths_7_QB.pdf (FREE)
- [ ] Physics_5_QB.pdf (FREE)

### 3. Test Locally
- [ ] Run `npm install` (if not already done)
- [ ] Run `npm run dev`
- [ ] Open `http://localhost:5173`
- [ ] Create a test account
- [ ] Test login/logout
- [ ] Test accessing free resources
- [ ] Test accessing paid resources with access codes
- [ ] Test download tracking

### 4. Verify Configuration
- [ ] Check `src/lib/accessCode.ts` for correct subjects
- [ ] Verify free resources list matches your PDFs
- [ ] Confirm all subjects have correct chapter counts

### 5. Build and Deploy
- [ ] Run `npm run build` to test production build
- [ ] Choose deployment platform (GitHub Pages, Netlify, Vercel)
- [ ] Follow deployment instructions in `DEPLOYMENT.md`
- [ ] Test deployed version

## 📋 Subject Configuration

Current configuration (already set up):

- **Maths**: 7 chapters
- **Physics**: 7 chapters
- **Chemistry**: 7 chapters
- **Biology**: 6 chapters
- **Social Science**: 9 chapters

## 🆓 Free Resources

Current free resources (already configured):

- Maths_6_QB
- Maths_7_QB
- Physics_5_QB
- History_4_QB

## 🔑 Finding Access Codes

To find access codes for your PDFs:

1. **Option 1**: Check `ACCESS_CODES.md` for complete list
2. **Option 2**: Open browser console (F12) and try to access a resource
3. **Option 3**: Use the formula: `MN` + first 5 chars of base64(fileKey)

## 🚀 Deployment Quick Links

### GitHub Pages
1. Push to GitHub
2. Settings → Pages → GitHub Actions
3. Done!

### Netlify
1. Connect GitHub repo
2. Build: `npm run build`
3. Publish: `dist`
4. Deploy!

### Vercel
1. Import GitHub repo
2. Framework: Vite
3. Deploy!

## 📚 Documentation Quick Links

- **Setup Guide**: `SETUP_GUIDE.md` - Comprehensive setup instructions
- **User Guide**: `USER_GUIDE.md` - End-user documentation
- **Access Codes**: `ACCESS_CODES.md` - Complete access code reference
- **Deployment**: `DEPLOYMENT.md` - Detailed deployment guide
- **PDF Guide**: `public/pdfs/README.md` - PDF naming conventions
- **Logo Guide**: `public/images/LOGO_INSTRUCTIONS.md` - Logo instructions

## ⚠️ Important Notes

### File Naming
- ✅ Case-sensitive: `Maths_1.pdf` not `maths_1.pdf`
- ✅ Use exact subject names: `Social Science_5.pdf` (with space)
- ✅ Use underscores: `Maths_1_QB.pdf` not `Maths-1-QB.pdf`

### Subject Names
- Maths (not Math or Mathematics)
- Physics
- Chemistry
- Biology
- Social Science (with space, not SocialScience)

### Free Resources
- Don't require access codes
- Automatically detected by the system
- Listed in `src/lib/accessCode.ts`

## 🆘 Troubleshooting

### PDF Not Loading
1. Check file name (case-sensitive)
2. Verify file is in `public/pdfs/`
3. Check browser console for errors
4. Try accessing directly: `http://localhost:5173/pdfs/Maths_1.pdf`

### Access Code Not Working
1. Check console for expected code
2. Verify exact spelling (case-sensitive)
3. Confirm resource isn't in free list

### Login Issues
1. Clear localStorage: `localStorage.clear()` in console
2. Create new account
3. Check console for errors

## ✨ You're Ready!

Once you've completed the checklist above, your Minimal Notes application is ready to use!

### Final Steps:
1. ✅ Test everything locally
2. ✅ Deploy to your chosen platform
3. ✅ Share with users
4. ✅ Enjoy!

---

**Need Help?** Check the documentation files listed above or review `SETUP_GUIDE.md` for detailed instructions.
