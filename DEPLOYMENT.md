# Deployment Guide - GitHub Pages

This guide explains how to deploy the Minimal Notes application to GitHub Pages.

## Prerequisites

- A GitHub account
- Git installed on your local machine
- Node.js and npm/pnpm installed

## Step 1: Prepare Your Repository

1. Create a new repository on GitHub (e.g., `minimal-notes`)
2. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/YOUR_USERNAME/minimal-notes.git
   cd minimal-notes
   ```

3. Copy all project files to the repository directory

## Step 2: Configure for GitHub Pages

1. Update `vite.config.ts` to set the base path:
   ```typescript
   export default defineConfig({
     base: '/minimal-notes/', // Replace with your repository name
     // ... rest of config
   });
   ```

2. If deploying to a custom domain, create a `CNAME` file in the `public` directory:
   ```
   yourdomain.com
   ```

## Step 3: Install Dependencies

```bash
pnpm install
# or
npm install
```

## Step 4: Build the Application

```bash
pnpm run build
# or
npm run build
```

This creates a `dist` directory with the production build.

## Step 5: Deploy to GitHub Pages

### Option A: Using gh-pages Package (Recommended)

1. Install gh-pages:
   ```bash
   pnpm add -D gh-pages
   # or
   npm install --save-dev gh-pages
   ```

2. Add deployment scripts to `package.json`:
   ```json
   {
     "scripts": {
       "predeploy": "pnpm run build",
       "deploy": "gh-pages -d dist"
     }
   }
   ```

3. Deploy:
   ```bash
   pnpm run deploy
   # or
   npm run deploy
   ```

### Option B: Manual Deployment

1. Build the application:
   ```bash
   pnpm run build
   ```

2. Create a `gh-pages` branch:
   ```bash
   git checkout --orphan gh-pages
   ```

3. Remove all files except the `dist` directory:
   ```bash
   git rm -rf .
   ```

4. Move contents of `dist` to root:
   ```bash
   mv dist/* .
   rm -rf dist
   ```

5. Commit and push:
   ```bash
   git add .
   git commit -m "Deploy to GitHub Pages"
   git push origin gh-pages
   ```

### Option C: GitHub Actions (Automated)

1. Create `.github/workflows/deploy.yml`:
   ```yaml
   name: Deploy to GitHub Pages

   on:
     push:
       branches: [ main ]

   jobs:
     build-and-deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         
         - name: Setup Node.js
           uses: actions/setup-node@v3
           with:
             node-version: '18'
             
         - name: Install pnpm
           uses: pnpm/action-setup@v2
           with:
             version: 8
             
         - name: Install dependencies
           run: pnpm install
           
         - name: Build
           run: pnpm run build
           
         - name: Deploy
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./dist
   ```

2. Commit and push:
   ```bash
   git add .github/workflows/deploy.yml
   git commit -m "Add GitHub Actions workflow"
   git push origin main
   ```

## Step 6: Configure GitHub Pages Settings

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select:
   - Branch: `gh-pages`
   - Folder: `/ (root)`
4. Click **Save**

## Step 7: Add PDF Files

Before or after deployment, add your PDF files:

1. Create the directory structure:
   ```
   public/pdfs/
   ```

2. Add PDF files following the naming convention:
   - Notes: `{Subject}_{Chapter}.pdf`
   - Question Bank: `{Subject}_{Chapter}_QB.pdf`
   - One Word: `{Subject}_{Chapter}_OW.pdf`

3. Commit and redeploy:
   ```bash
   git add public/pdfs/
   git commit -m "Add PDF files"
   git push origin main
   pnpm run deploy
   ```

## Step 8: Access Your Site

Your site will be available at:
- `https://YOUR_USERNAME.github.io/minimal-notes/`
- Or your custom domain if configured

## Troubleshooting

### Blank Page After Deployment

**Problem**: The page loads but shows a blank screen.

**Solution**: 
- Ensure `base` in `vite.config.ts` matches your repository name
- Check browser console for 404 errors
- Verify the `gh-pages` branch contains the built files

### 404 Errors for Routes

**Problem**: Direct navigation to routes (e.g., `/dashboard`) returns 404.

**Solution**: 
- GitHub Pages doesn't support client-side routing by default
- Add a `404.html` file that redirects to `index.html`:
  ```html
  <!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <title>Minimal Notes</title>
      <script>
        sessionStorage.redirect = location.href;
      </script>
      <meta http-equiv="refresh" content="0;URL='/'">
    </head>
    <body></body>
  </html>
  ```

- Update `index.html` to handle the redirect:
  ```html
  <script>
    (function(){
      var redirect = sessionStorage.redirect;
      delete sessionStorage.redirect;
      if (redirect && redirect != location.href) {
        history.replaceState(null, null, redirect);
      }
    })();
  </script>
  ```

### PDF Files Not Loading

**Problem**: PDFs return 404 errors.

**Solution**:
- Verify PDF files are in `public/pdfs/` directory
- Check file names match the expected format
- Ensure files are committed and pushed to the repository
- Rebuild and redeploy after adding files

### Access Codes Not Working

**Problem**: Valid access codes are rejected.

**Solution**:
- Open browser console to see the expected access code
- Ensure codes are entered in uppercase
- Verify the access code generation logic matches the file key

## Updating the Site

To update your deployed site:

1. Make changes to your code
2. Commit the changes:
   ```bash
   git add .
   git commit -m "Your update message"
   git push origin main
   ```
3. Redeploy:
   ```bash
   pnpm run deploy
   ```

## Custom Domain Setup

1. Add a `CNAME` file to the `public` directory with your domain:
   ```
   notes.yourdomain.com
   ```

2. Configure DNS records with your domain provider:
   - Type: `CNAME`
   - Name: `notes` (or `@` for root domain)
   - Value: `YOUR_USERNAME.github.io`

3. In GitHub repository settings:
   - Go to **Settings** → **Pages**
   - Enter your custom domain
   - Enable **Enforce HTTPS**

## Performance Optimization

1. **Enable Compression**: GitHub Pages automatically serves gzip-compressed files

2. **Optimize Images**: Compress any images before deployment

3. **Lazy Loading**: The application already implements lazy loading for routes

4. **Caching**: Configure appropriate cache headers in your hosting settings

## Security Considerations

1. **HTTPS**: Always enable HTTPS in GitHub Pages settings

2. **Content Security Policy**: Consider adding CSP headers

3. **Password Storage**: 
   - Current implementation uses localStorage (for demonstration)
   - For production, implement proper backend authentication
   - Consider using services like Firebase Auth or Supabase

## Monitoring

1. **GitHub Pages Status**: Check https://www.githubstatus.com/

2. **Analytics**: Add Google Analytics or similar:
   ```html
   <!-- Add to index.html -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
   <script>
     window.dataLayer = window.dataLayer || [];
     function gtag(){dataLayer.push(arguments);}
     gtag('js', new Date());
     gtag('config', 'GA_MEASUREMENT_ID');
   </script>
   ```

## Backup

Regularly backup your repository:
```bash
git clone --mirror https://github.com/YOUR_USERNAME/minimal-notes.git
```

## Support

For GitHub Pages specific issues:
- GitHub Pages Documentation: https://docs.github.com/en/pages
- GitHub Community Forum: https://github.community/

---

**Note**: This deployment guide assumes you're using the default project structure. Adjust paths and commands as needed for your specific setup.
