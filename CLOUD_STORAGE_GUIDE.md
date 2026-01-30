# Cloud Storage Integration Guide

The Anaesthetic Logbook can sync with cloud storage services for automatic backups. There are two approaches:

## Option 1: Simple Manual Sync (Recommended for Most Users)

**No setup required!** Just use the built-in export/import:

### Google Drive
1. Click "Export as JSON"
2. Upload to Google Drive manually
3. Access from any device
4. Import when needed

**Pros:**
- ✅ No technical setup
- ✅ Works immediately
- ✅ Complete control
- ✅ No OAuth complexity

**Cons:**
- ⚠️ Manual process (click to sync)
- ⚠️ Must remember to export

### Dropbox / Box
Same process - export JSON and upload manually.

---

## Option 2: Automatic Cloud Sync (Advanced)

For automatic syncing, you need to set up OAuth authentication. This requires technical knowledge.

### Current Status

The app has the **UI and framework** for cloud sync, but requires **OAuth credentials** to function. 

**Why?** 
- Cloud services require authentication for security
- Each user/organization needs their own API credentials
- Cannot include working credentials in public code (security risk)

### Setting Up OAuth (For Developers/IT Admins)

If you want automatic cloud sync, you'll need to:

#### Google Drive Setup

1. **Create Google Cloud Project**
   - Go to https://console.cloud.google.com
   - Create new project: "Anaesthetic Logbook"
   
2. **Enable Google Drive API**
   - In APIs & Services → Library
   - Search "Google Drive API"
   - Click Enable

3. **Create OAuth Credentials**
   - APIs & Services → Credentials
   - Create OAuth 2.0 Client ID
   - Application type: Web application
   - Authorized origins: Your app URL
   - Authorized redirect URIs: Your app URL + `/callback`

4. **Get Credentials**
   - Copy Client ID
   - Copy Client Secret

5. **Add to App**
   ```javascript
   const GOOGLE_CLIENT_ID = 'your-client-id-here';
   const GOOGLE_CLIENT_SECRET = 'your-secret-here';
   const REDIRECT_URI = 'your-app-url/callback';
   ```

6. **Implement OAuth Flow**
   - See `cloud-oauth-example.js` for implementation
   - Handle token refresh
   - Store tokens securely

#### Dropbox Setup

1. **Create Dropbox App**
   - Go to https://www.dropbox.com/developers/apps
   - Create app → Scoped access
   - Choose "Full Dropbox" or "App folder"
   - Name: "Anaesthetic Logbook"

2. **Configure OAuth**
   - Add redirect URI
   - Set permissions: `files.content.write`, `files.content.read`

3. **Get Credentials**
   - Copy App key
   - Copy App secret

4. **Implement**
   ```javascript
   const DROPBOX_CLIENT_ID = 'your-app-key';
   const DROPBOX_CLIENT_SECRET = 'your-app-secret';
   ```

#### Box Setup

1. **Create Box App**
   - Go to https://app.box.com/developers/console
   - Create New App → Custom App
   - Authentication: OAuth 2.0 with JWT

2. **Configure**
   - Add redirect URI
   - Set scopes: Read and write all files

3. **Get Credentials**
   - Copy Client ID
   - Copy Client Secret

---

## Recommended Approach by User Type

### Individual Doctor
**Use:** Manual export to Google Drive
- Export weekly to Google Drive folder
- Set phone reminder
- 5 minutes per week
- 100% reliable

### Small Practice (2-10 doctors)
**Use:** Shared Google Drive folder
- Each exports to shared folder
- Monthly review
- Simple and effective

### Hospital Department
**Use:** IT-managed solution with OAuth
- Contact IT department
- Set up OAuth properly
- Automatic sync for all users
- Requires ongoing IT support

### Medical School
**Use:** Hosted solution
- Consider professional logbook service
- Or custom deployment with IT team
- Centralized management

---

## Security Considerations

### Manual Export (Option 1)
- ✅ You control where files go
- ✅ No API keys to manage
- ✅ No access tokens to secure
- ✅ Works offline

### OAuth Sync (Option 2)
- ⚠️ Access tokens need secure storage
- ⚠️ Tokens can expire (need refresh)
- ⚠️ API rate limits apply
- ⚠️ Requires HTTPS in production
- ⚠️ User must authorize access

---

## Implementation Status

### ✅ Already Working
- Manual JSON export
- Manual JSON import
- PDF export
- Excel export
- CSV export
- Local storage

### 🔧 Requires OAuth Setup
- Automatic Google Drive sync
- Automatic Dropbox sync
- Automatic Box sync
- Auto-sync on save

### 📋 To Implement (If You Set Up OAuth)

Replace the placeholder functions in the app with actual OAuth flows:

```javascript
// Example: Real Google Drive upload
async function uploadToGoogleDrive(data) {
    const metadata = {
        name: cloudConfig.fileName,
        mimeType: 'application/json'
    };
    
    const form = new FormData();
    form.append('metadata', new Blob([JSON.stringify(metadata)], {type: 'application/json'}));
    form.append('file', new Blob([data], {type: 'application/json'}));
    
    const response = await fetch('https://www.googleapis.com/upload/drive/v3/files?uploadType=multipart', {
        method: 'POST',
        headers: {
            'Authorization': `Bearer ${cloudConfig.accessToken}`
        },
        body: form
    });
    
    if (!response.ok) throw new Error('Upload failed');
    return await response.json();
}
```

---

## Quick Decision Guide

**Just want backups?**
→ Use manual JSON export to Google Drive

**Want automatic sync?**
→ Need IT support for OAuth setup

**Hospital/institution?**
→ Contact IT department for proper deployment

**Don't have IT support?**
→ Stick with manual export (it's actually very quick!)

---

## Support Resources

### For OAuth Implementation
- [Google Drive API Docs](https://developers.google.com/drive/api/guides/about-sdk)
- [Dropbox API Docs](https://www.dropbox.com/developers/documentation)
- [Box API Docs](https://developer.box.com/guides/)

### For Questions
- Open a GitHub issue
- Tag as "cloud-sync"
- Specify which service (Google/Dropbox/Box)

---

## Privacy & Data Protection

### What Gets Synced?
- JSON file with all your cases
- No additional metadata
- Encrypted in transit (HTTPS)
- Stored in your cloud account (you control it)

### What Doesn't Get Synced?
- App settings (themes, etc.) - stays local
- Supervisor names list - stays local
- Location autocomplete - stays local

### GDPR Compliance
- You control the data destination
- You can delete anytime
- No third-party access
- You own the cloud account

---

**Bottom Line:** For most users, manual export every week is simpler, faster to set up, and more reliable than OAuth sync. The 2 minutes per week is worth avoiding the OAuth complexity!
