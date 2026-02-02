# Quick Setup: Offline CDN Files

## 🎯 Goal
Make your app work 100% offline by downloading JavaScript libraries locally.

## 📥 Method 1: Download via Browser (Easiest)

### Step 1: Download the Files

**Click these links and save each file:**

1. **jsPDF** (PDF generation):
   - URL: https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js
   - Right-click → Save As → `jspdf.umd.min.js`

2. **jsPDF-AutoTable** (PDF tables):
   - URL: https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js
   - Right-click → Save As → `jspdf.plugin.autotable.min.js`

3. **SheetJS** (Excel generation):
   - URL: https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js
   - Right-click → Save As → `xlsx.full.min.js`

### Step 2: Organize Your Files

Create a folder with this structure:
```
anaesthetic-logbook/
  ├── index.html              (your main HTML file, renamed)
  ├── jspdf.umd.min.js
  ├── jspdf.plugin.autotable.min.js
  └── xlsx.full.min.js
```

### Step 3: Update index.html

**Find these lines near the bottom of index.html:**
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
```

**Replace with:**
```html
<script src="jspdf.umd.min.js"></script>
<script src="jspdf.plugin.autotable.min.js"></script>
<script src="xlsx.full.min.js"></script>
```

**Save the file.**

---

## 📥 Method 2: Command Line (For Developers)

```bash
# Create project folder
mkdir anaesthetic-logbook
cd anaesthetic-logbook

# Download files
curl -o jspdf.umd.min.js https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js
curl -o jspdf.plugin.autotable.min.js https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js
curl -o xlsx.full.min.js https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js

# Copy your HTML file and rename
cp /path/to/anaesthetic-logbook.html index.html

# Edit index.html and update the script tags (see Step 3 above)
```

---

## ☁️ Upload to GitHub Pages

```bash
# Initialize git
git init
git add .
git commit -m "Add offline support"

# Create GitHub repo and push
git remote add origin https://github.com/YOUR-USERNAME/anaesthetic-logbook.git
git branch -M main
git push -u origin main

# Enable GitHub Pages
# Go to: Settings → Pages
# Source: main branch
# Save
```

Your app will be at: `https://YOUR-USERNAME.github.io/anaesthetic-logbook/`

---

## ☁️ Upload to Netlify

**Easiest option:**
1. Go to https://app.netlify.com/drop
2. Drag all 4 files into the drop zone
3. Get instant URL: `https://random-name.netlify.app`
4. Done!

**To keep it permanent:**
- Sign up for free Netlify account
- Claim the site
- Get custom domain (optional)

---

## ✅ Test Offline Mode

### On Desktop:
1. Open app in Chrome/Firefox
2. Press F12 (Developer Tools)
3. Go to "Network" tab
4. Check "Offline" box
5. Refresh page
6. Try exporting PDF/Excel
7. Should work! ✅

### On iPhone:
1. Add app to home screen
2. Turn on Airplane Mode
3. Open app from home screen
4. Add a test case
5. Export to PDF
6. Should work! ✅

---

## 🔍 Troubleshooting

### "Uncaught ReferenceError: jsPDF is not defined"
**Problem:** Files not loading or wrong path
**Fix:** 
- Check all 3 .js files are in same folder as index.html
- Check script tags have correct filenames
- Check no typos in filenames

### "PDF export shows blank page"
**Problem:** jsPDF-AutoTable not loaded
**Fix:**
- Make sure `jspdf.plugin.autotable.min.js` loads AFTER `jspdf.umd.min.js`
- Order matters!

### "Excel export not working"
**Problem:** SheetJS not loaded
**Fix:**
- Check `xlsx.full.min.js` exists
- Check script tag path is correct

### "Works on WiFi but not offline"
**Problem:** Still loading from CDN
**Fix:**
- Open browser DevTools
- Network tab → reload page
- Look for any requests to cdnjs.cloudflare.com
- If you see any, you didn't update the script tags

---

## 📦 File Sizes (FYI)

- jspdf.umd.min.js: ~200 KB
- jspdf.plugin.autotable.min.js: ~45 KB
- xlsx.full.min.js: ~800 KB

**Total: ~1 MB** (very reasonable for offline capability)

---

## 🎉 What You Gain

✅ Works in hospitals with poor WiFi
✅ Works on planes, trains, anywhere
✅ Faster loading (no CDN latency)
✅ No dependency on third-party servers
✅ App is truly self-contained

---

## 🚀 Next Steps

After getting offline working:

1. **Add to iPhone home screen**
2. **Test in Airplane Mode**
3. **Set weekly backup reminder**
4. **Use it in real clinical practice**

---

## 💾 Backup the Offline Files

These files change rarely, but when you update:
1. Keep old versions in a backup folder
2. Test new versions before replacing
3. Document which version you're using

Current versions:
- jsPDF: 2.5.1
- jsPDF-AutoTable: 3.5.31
- SheetJS: 0.18.5

---

**Done! Your app now works 100% offline.** 🎊

**Test it right now:**
1. Turn off WiFi
2. Open your app
3. Export a PDF
4. If it works → Success! ✅
