# Deployment Guide

## Quick Deploy Options

### Option 1: Vercel (Recommended - Easiest)

1. **Push your code to GitHub:**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin YOUR_GITHUB_REPO_URL
   git push -u origin main
   ```

2. **Deploy on Vercel:**
   - Go to https://vercel.com
   - Sign up/Login with GitHub
   - Click "Add New Project"
   - Import your repository
   - Vercel will auto-detect Vite settings
   - Click "Deploy"
   - Your site will be live in ~2 minutes!

3. **Custom Domain (Optional):**
   - In Vercel dashboard, go to Settings → Domains
   - Add your custom domain

---

### Option 2: Netlify

1. **Push to GitHub** (same as above)

2. **Deploy on Netlify:**
   - Go to https://netlify.com
   - Sign up/Login with GitHub
   - Click "Add new site" → "Import an existing project"
   - Select your repository
   - Build settings:
     - **Build command:** `npm run build`
     - **Publish directory:** `build`
   - Click "Deploy site"

---

### Option 3: GitHub Pages

1. **Install gh-pages:**
   ```bash
   npm install --save-dev gh-pages
   ```

2. **Add to package.json scripts:**
   ```json
   "scripts": {
     "predeploy": "npm run build",
     "deploy": "gh-pages -d build"
   }
   ```

3. **Update vite.config.ts:**
   ```typescript
   export default defineConfig({
     // ... existing config
     base: '/your-repo-name/', // Replace with your GitHub repo name
   });
   ```

4. **Deploy:**
   ```bash
   npm run deploy
   ```

5. **Enable GitHub Pages:**
   - Go to your repo → Settings → Pages
   - Source: `gh-pages` branch
   - Your site will be at: `https://yourusername.github.io/your-repo-name/`

---

## Before Deploying

### 1. Set up Web3Forms (for Contact Form)
1. Go to https://web3forms.com
2. Sign up for free
3. Get your access key
4. Create `.env` file in project root:
   ```
   VITE_WEB3FORMS_ACCESS_KEY=your_access_key_here
   ```
5. Add `.env` to `.gitignore` (don't commit your key!)

### 2. Environment Variables on Hosting Platform

**For Vercel:**
- Go to Project Settings → Environment Variables
- Add: `VITE_WEB3FORMS_ACCESS_KEY` = your key
- Redeploy

**For Netlify:**
- Go to Site Settings → Environment Variables
- Add: `VITE_WEB3FORMS_ACCESS_KEY` = your key
- Redeploy

---

## Build Locally First (Test)

```bash
npm run build
```

This creates a `build` folder with your production-ready site.

---

## Need Help?

- **Vercel Docs:** https://vercel.com/docs
- **Netlify Docs:** https://docs.netlify.com
- **GitHub Pages Docs:** https://pages.github.com

