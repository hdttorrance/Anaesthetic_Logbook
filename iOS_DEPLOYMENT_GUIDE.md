# iOS Deployment Guide - Critical Fixes Applied

## ✅ What's Already Fixed in the Code (v2.2.0)

### 1. **Input Zoom Prevention** ✅
- All inputs now use `font-size: 16px` (not 1rem)
- Prevents iOS auto-zoom when tapping input fields
- **Impact**: No more annoying zoom-in during case entry

### 2. **Safe Area (Notch) Support** ✅
- Header uses `env(safe-area-inset-top/left/right)`
- Title won't be hidden behind notch/clock
- **Impact**: Readable on iPhone X, 11, 12, 13, 14, 15, 16

### 3. **Swipe-Back Prevention** ✅
- Body has `overscroll-behavior-x: none`
- Prevents accidental navigation swipe
- **Impact**: Won't lose form data from accidental swipes

### 4. **7-Day Backup Warning System** ✅
- Red warning banner appears if no backup in 7+ days
- Export tab highlights in red
- Automatic timestamp on every export
- **Impact**: Reminds users before iOS deletes data

### 5. **PII Disclaimer** ✅
- Modal on first load explaining privacy
- Warns about jigsaw identification risk
- **Impact**: Legal protection, user awareness

### 6. **iOS-Optimized Viewport** ✅
- `viewport-fit=cover` for full screen
- Removed `user-scalable=no` for accessibility
- **Impact**: Better iOS PWA experience

---

## ⚠️ Critical Issues That Still Need Manual Action

### Issue 1: localStorage Data Loss Risk

**The Problem:**
- iOS **will delete** localStorage if:
  - Device is low on storage
  - App not opened for 7+ days
  - User clears Safari data
  - Private browsing mode
- **You will lose ALL cases with zero warning**

**Current Mitigation:**
- ✅ 7-day backup warning implemented
- ✅ Multiple export options (JSON, Email, Files)
- ⚠️ Still relies on user remembering to backup

**The ONLY Real Fix:**
Use Capacitor with Storage Plugin (see Section 3 below)

---

### Issue 2: Offline CDN Dependency

**The Problem:**
Your app loads these from CDNs:
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
```

**The Risk:**
- No hospital WiFi = Can't export PDFs/Excel
- No internet = App partially broken
- CDN goes down = Exports fail

**The Fix: Download Local Copies**

#### Step-by-step:

**1. Download the files:**

```bash
# Create a folder for your app
mkdir anaesthetic-logbook-offline
cd anaesthetic-logbook-offline

# Download jsPDF
curl -o jspdf.umd.min.js https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js

# Download jsPDF-AutoTable
curl -o jspdf.plugin.autotable.min.js https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.31/jspdf.plugin.autotable.min.js

# Download SheetJS
curl -o xlsx.full.min.js https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js
```

**2. Update your HTML file:**

Find these lines in your HTML (near the bottom, before `</body>`):
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

**3. Upload all files together:**
```
anaesthetic-logbook-offline/
  ├── index.html  (your main file, renamed)
  ├── jspdf.umd.min.js
  ├── jspdf.plugin.autotable.min.js
  └── xlsx.full.min.js
```

**For GitHub Pages:**
- Upload ALL 4 files to your repository
- GitHub Pages will serve them together

**For Netlify:**
- Drag all 4 files into Netlify Drop
- Done!

**Result:** App now works 100% offline ✅

---

### Issue 3: File Saving on Native App

**The Problem:**
Current code uses:
```javascript
const link = document.createElement('a');
link.href = url;
link.download = 'filename.json';
link.click();
```

This works in Safari PWA but **might fail** in a Capacitor-wrapped App Store app.

**The Fix:**
Only needed if you go the native app route (see Section 3).

---

## 🚀 Option 1: Deploy as PWA (Recommended for Most Users)

### What You Get:
✅ Works immediately (10 minute setup)
✅ All iOS fixes active
✅ Email/Files backup works
✅ No developer account needed
✅ Free forever

### What You Don't Get:
⚠️ localStorage still vulnerable
⚠️ Can't publish to App Store
⚠️ Users must manually add to home screen

### Setup Steps:

**1. Download offline CDN files** (see Issue 2 above)

**2. Host on GitHub Pages:**
```bash
# Upload these files to GitHub:
- index.html (your main file)
- jspdf.umd.min.js
- jspdf.plugin.autotable.min.js
- xlsx.full.min.js
```

**3. Test on iPhone:**
```
1. Safari → your-username.github.io/anaesthetic-logbook
2. Share → Add to Home Screen
3. Test: Turn on Airplane Mode
4. Open app → Try exporting PDF
5. Should work offline! ✅
```

---

## 📱 Option 2: Native App with Capacitor (Solves ALL Issues)

### What You Get:
✅ Real file system storage (no localStorage deletion)
✅ Proper file saving to iPhone Files app
✅ Can publish to App Store
✅ Works 100% offline (no CDN dependency)
✅ Better iOS integration

### What You Need:
- Mac computer (for Xcode)
- Apple Developer account ($99/year for App Store)
- Basic command line knowledge
- 2-3 hours for first setup

### Complete Setup Guide:

#### Step 1: Install Prerequisites

```bash
# Install Node.js from nodejs.org (if not installed)
node --version  # Should show v18 or higher

# Install Capacitor CLI
npm install -g @capacitor/cli
```

#### Step 2: Create Capacitor Project

```bash
# Create project folder
mkdir AnaestheticLogbook
cd AnaestheticLogbook

# Initialize Capacitor
npm init -y
npm install @capacitor/core @capacitor/cli
npx cap init

# Answer prompts:
# App name: Anaesthetic Logbook
# App ID: com.yourname.logbook  (must be unique)
# Web directory: www
```

#### Step 3: Prepare Your Files

```bash
# Create www directory
mkdir www

# Copy your files:
# - Rename anaesthetic-logbook.html to index.html
# - Copy to www/index.html
# - Copy all .js files to www/

# Your structure should be:
# www/
#   ├── index.html
#   ├── jspdf.umd.min.js
#   ├── jspdf.plugin.autotable.min.js
#   └── xlsx.full.min.js
```

#### Step 4: Install Storage Plugin

```bash
# Install Capacitor Storage (replaces localStorage)
npm install @capacitor/preferences
```

#### Step 5: Update Your Code for Capacitor Storage

In your `index.html`, add after the other script tags:

```html
<script>
// Capacitor Storage wrapper (replaces localStorage)
if (typeof Capacitor !== 'undefined') {
    const { Preferences } = Capacitor.Plugins;
    
    // Override localStorage with Capacitor Preferences
    const originalSetItem = localStorage.setItem.bind(localStorage);
    const originalGetItem = localStorage.getItem.bind(localStorage);
    
    localStorage.setItem = async function(key, value) {
        await Preferences.set({ key, value });
        originalSetItem(key, value); // Keep in memory for speed
    };
    
    localStorage.getItem = async function(key) {
        const { value } = await Preferences.get({ key });
        return value;
    };
}
</script>
```

#### Step 6: Add iOS Platform

```bash
# Add iOS platform
npx cap add ios

# This creates ios/ folder with Xcode project
```

#### Step 7: Configure iOS Settings

Edit `capacitor.config.json`:
```json
{
  "appId": "com.yourname.logbook",
  "appName": "Anaesthetic Logbook",
  "webDir": "www",
  "ios": {
    "contentInset": "always"
  }
}
```

#### Step 8: Open in Xcode

```bash
# Open Xcode project
npx cap open ios
```

In Xcode:
1. Select your project in left panel
2. Under "Signing & Capabilities"
   - Team: Select your Apple Developer account
   - Bundle Identifier: Should match your appId
3. Under "Deployment Info"
   - Minimum iOS: 13.0
   - Device: iPhone, iPad

#### Step 9: Build and Test

1. Connect iPhone via USB
2. Select your iPhone in Xcode device dropdown
3. Click ▶️ (Run)
4. App installs on your iPhone
5. Test:
   - Add a case
   - Close app completely
   - Wait 24 hours
   - Open app → Data still there! ✅

#### Step 10: Publish to App Store (Optional)

```bash
# Build for release
1. Xcode → Product → Archive
2. Upload to App Store Connect
3. Create app listing
4. Submit for review
5. Wait 1-3 days
6. App appears in App Store
```

---

## 📊 Comparison: PWA vs Native

| Feature | PWA (GitHub Pages) | Native (Capacitor) |
|---------|-------------------|-------------------|
| **Setup Time** | 30 minutes | 3 hours |
| **Cost** | Free | $99/year |
| **Data Safety** | ⚠️ localStorage vulnerable | ✅ Permanent storage |
| **Offline Exports** | ✅ With local .js files | ✅ Always |
| **App Store** | ❌ No | ✅ Yes |
| **Updates** | Upload new HTML | Rebuild & resubmit |
| **Requirements** | Any computer | Mac + Xcode |

---

## 🆘 Emergency Data Recovery

### If localStorage is deleted:

**Check Email:**
1. Search email for "Anaesthetic Logbook Backup"
2. Download JSON attachment
3. Open app → Export tab → Import Data

**Check Files:**
1. iPhone Files app → iCloud Drive
2. Look for backup JSON files
3. Import in app

**Prevent Next Time:**
1. Set iPhone reminder: "Backup Logbook" every Sunday
2. Email to yourself weekly
3. Keep copies in multiple places

---

## 🎯 Recommended Approach

### For Personal Use (You Only):
**→ PWA + Weekly Backups**
- 30 minute setup
- Free forever
- Just remember to backup weekly
- Set phone reminder!

### For Department/Team:
**→ Capacitor Native App**
- One-time setup by IT
- Distribute via App Store (or TestFlight)
- Users' data is safe
- Professional solution

---

## 📋 Pre-Flight Checklist

Before deploying, verify:

**PWA Checklist:**
- [ ] Downloaded all 3 .js files locally
- [ ] Updated script tags to local paths
- [ ] Tested offline mode (Airplane Mode)
- [ ] Verified exports work offline
- [ ] Added to iPhone home screen
- [ ] Tested on actual iPhone with notch
- [ ] Set weekly backup reminder

**Capacitor Checklist:**
- [ ] Mac with Xcode installed
- [ ] Apple Developer account
- [ ] Storage plugin installed
- [ ] localStorage wrapper implemented
- [ ] Built and tested on real iPhone
- [ ] Data persists after 24 hours
- [ ] App icons created (180x180, 1024x1024)
- [ ] Bundle ID is unique

---

## 💡 Pro Tips

### For PWA Users:
1. **Set TWO reminders:**
   - Sunday 8pm: Backup logbook
   - First of month: Verify backup works
   
2. **Use multiple backup methods:**
   - Email to Gmail (Google cloud)
   - Email to Outlook (Microsoft cloud)
   - Save to Files → iCloud Drive
   
3. **Before holidays/breaks:**
   - Export to JSON
   - Email to yourself
   - Don't open app for weeks? Data might be gone!

### For Native App Developers:
1. **Use TestFlight first:**
   - Internal testing with 100 users
   - Get feedback before public release
   
2. **Version your data:**
   ```javascript
   const DATA_VERSION = "2.2.0";
   // Save with each export
   // Check on import for compatibility
   ```
   
3. **Add crash reporting:**
   - Sentry.io (free tier)
   - See if users are losing data

---

## 🔧 Troubleshooting

### "App zooms in when I tap inputs"
→ Make sure font-size is **exactly** 16px (not 16.5px, not 1rem)

### "Title is behind the notch"
→ Check `.app-header` has `env(safe-area-inset-top)`

### "Data disappeared after a week"
→ iOS deleted localStorage. Use backups or switch to Capacitor.

### "Can't export PDFs offline"
→ You're still using CDN links. Download .js files locally.

### "Swipe gesture closes the app"
→ Add `overscroll-behavior-x: none` to body CSS

### "Capacitor build fails"
→ Check Xcode signing settings, bundle ID must be unique

---

## 📞 Need Help?

**For PWA Issues:**
- Check browser console for errors
- Test in private browsing first
- Clear cache and try again

**For Capacitor Issues:**
- Check Capacitor docs: capacitorjs.com
- Xcode console shows detailed errors
- Stack Overflow: "capacitor ios [your error]"

**For Data Loss:**
- Prevention > Recovery
- BACKUP WEEKLY
- Set reminder NOW

---

## ✅ Summary

**Already Fixed in Code:**
✅ Input zoom prevention (16px fonts)
✅ Notch support (safe-area-insets)
✅ Swipe-back prevention
✅ 7-day backup warnings
✅ PII disclaimer

**You Must Do:**
1. Download .js files for offline use
2. Choose PWA or Capacitor
3. Set weekly backup reminder
4. Test on actual iPhone

**Critical Warning:**
iOS **WILL** delete localStorage. The only 100% safe solution is:
1. Capacitor with Storage plugin, OR
2. Religious weekly backups to email/cloud

Don't let 6 months of cases disappear! 🚨

---

**Ready to deploy?** Start with the PWA route, test it for a month, then decide if you need Capacitor.
