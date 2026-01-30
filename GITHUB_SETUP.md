# GitHub Setup Guide

This document provides step-by-step instructions for uploading the Anaesthetic Logbook to GitHub and deploying it.

## Prerequisites

- GitHub account (free at https://github.com)
- Git installed on your computer (download from https://git-scm.com)
- Basic command line knowledge (optional - can use GitHub Desktop instead)

## Method 1: Using GitHub Website (Easiest)

### Step 1: Create New Repository

1. Go to https://github.com and log in
2. Click the **"+"** icon in the top right
3. Select **"New repository"**
4. Fill in the details:
   - **Repository name:** `anaesthetic-logbook`
   - **Description:** "RCoA-compliant anaesthetic case logging PWA"
   - **Public or Private:** Choose based on your preference
   - **DO NOT** initialize with README (we already have one)
5. Click **"Create repository"**

### Step 2: Upload Files

1. On the new repository page, click **"uploading an existing file"**
2. Drag and drop ALL the files from the outputs folder:
   - `anaesthetic-logbook.html`
   - `index.html`
   - `README.md`
   - `LICENSE`
   - `CONTRIBUTING.md`
   - `CHANGELOG.md`
   - `INSTALLATION.md`
   - `.gitignore`
   - `.github/` folder (with workflows inside)
3. Add commit message: "Initial commit - Anaesthetic Logbook v1.0.0"
4. Click **"Commit changes"**

### Step 3: Enable GitHub Pages

1. Go to repository **Settings**
2. Scroll to **"Pages"** in the left sidebar
3. Under "Build and deployment":
   - **Source:** Deploy from a branch
   - **Branch:** main
   - **Folder:** / (root)
4. Click **"Save"**
5. Wait 2-3 minutes
6. Your app will be live at: `https://your-username.github.io/anaesthetic-logbook/`

## Method 2: Using Command Line (Recommended for Developers)

### Step 1: Create Repository on GitHub
Follow "Method 1 - Step 1" above to create the repository on GitHub.

### Step 2: Initialize Local Repository

Open Terminal (Mac/Linux) or Command Prompt (Windows) and navigate to the folder containing all the files:

```bash
cd path/to/your/files

# Initialize git repository
git init

# Add all files
git add .

# Create first commit
git commit -m "Initial commit - Anaesthetic Logbook v1.0.0"

# Connect to GitHub (replace YOUR-USERNAME and REPO-NAME)
git remote add origin https://github.com/YOUR-USERNAME/anaesthetic-logbook.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 3: Enable GitHub Pages
Follow "Method 1 - Step 3" above.

## Method 3: Using GitHub Desktop (User-Friendly)

### Step 1: Install GitHub Desktop
Download from https://desktop.github.com

### Step 2: Create Repository
1. Open GitHub Desktop
2. Click **"Create a New Repository on your hard drive"**
3. Name: `anaesthetic-logbook`
4. Local Path: Choose where to save
5. Click **"Create Repository"**

### Step 3: Add Files
1. Copy all files into the repository folder
2. GitHub Desktop will show all changes
3. Add commit message: "Initial commit - Anaesthetic Logbook v1.0.0"
4. Click **"Commit to main"**

### Step 4: Publish to GitHub
1. Click **"Publish repository"**
2. Choose public or private
3. Click **"Publish repository"**

### Step 5: Enable GitHub Pages
Follow "Method 1 - Step 3" above.

## Verifying Your Deployment

### Check if Files Uploaded Correctly
1. Go to your repository on GitHub
2. You should see all files listed
3. Click on `README.md` to verify it displays correctly

### Check if GitHub Pages is Working
1. Go to Settings → Pages
2. You should see: "Your site is live at https://..."
3. Click the link
4. You should be redirected to the app
5. Test that the app loads and works correctly

### Troubleshooting

**"404 - Page not found"**
- Wait a few more minutes (can take up to 10 minutes initially)
- Check that GitHub Pages is enabled
- Verify the branch is set to "main"

**App loads but doesn't work**
- Check browser console for errors (F12)
- Verify all files uploaded correctly
- Try clearing browser cache

**Changes not appearing**
- GitHub Pages can take 1-5 minutes to update
- Force refresh: Ctrl+Shift+R (Windows) or Cmd+Shift+R (Mac)

## Updating Your Repository

### Using GitHub Website
1. Navigate to the file you want to change
2. Click the pencil icon (Edit)
3. Make changes
4. Click "Commit changes"

### Using Command Line
```bash
# Make your changes to files
# Then:
git add .
git commit -m "Description of changes"
git push
```

### Using GitHub Desktop
1. Make changes to files
2. GitHub Desktop will show changes
3. Add commit message
4. Click "Commit to main"
5. Click "Push origin"

## Sharing Your Logbook

Once deployed, you can share your logbook:

**Public URL:** `https://your-username.github.io/anaesthetic-logbook/`

**Custom Domain (Optional):**
1. Purchase a domain name
2. Follow GitHub's custom domain guide
3. Example: `logbook.yourdomain.com`

## Privacy Considerations

### If Repository is Public
- ✅ Anyone can view and copy the CODE
- ✅ Your DATA remains private (stored locally in browser)
- ✅ Others can use the app but have their own separate data
- ⚠️ Do not commit any files with patient data

### If Repository is Private
- 🔒 Only you (and collaborators you invite) can see the code
- 🔒 Still secure for personal use
- 💰 May require GitHub Pro for private Pages (or use locally)

## Repository Management

### Good Practices
- ✅ Regular commits with clear messages
- ✅ Use branches for experimental features
- ✅ Tag releases (v1.0.0, v1.1.0, etc.)
- ✅ Keep README updated
- ✅ Respond to issues if making public

### Creating Releases
1. Go to repository page
2. Click "Releases" → "Create a new release"
3. Tag: `v1.0.0`
4. Title: "Version 1.0.0 - Initial Release"
5. Description: Copy from CHANGELOG.md
6. Attach `anaesthetic-logbook.html` as download
7. Click "Publish release"

## Backup Strategy

Even with GitHub:
- 📥 Keep local backups of your DATA (not just code)
- 💾 Regular JSON exports from the app
- 🔄 Multiple storage locations for critical data

## Next Steps

After setup:
1. ✅ Test the deployed app thoroughly
2. ✅ Bookmark your GitHub Pages URL
3. ✅ Set up regular backup routine
4. ✅ Consider making repository public to help others
5. ✅ Star your own repository for easy access

## Support

- **GitHub Docs:** https://docs.github.com
- **GitHub Pages Docs:** https://docs.github.com/en/pages
- **Git Tutorial:** https://git-scm.com/book/en/v2

---

**Important:** GitHub hosts your APPLICATION CODE, not your case data. Your data remains private in your browser's local storage.
