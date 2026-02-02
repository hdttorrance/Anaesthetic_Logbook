# Anaesthetic Logbook App

A comprehensive Progressive Web App (PWA) for anaesthetists to log and manage their clinical cases in accordance with RCoA (Royal College of Anaesthetists) guidelines for GMC revalidation.

![Version](https://img.shields.io/badge/version-2.2.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## Features

### 📋 Complete Case Logging
- Full RCoA logbook fields including:
  - Patient demographics (age, sex, ASA grade)
  - **Location tracking** (where case was performed) with autocomplete
  - **Hospital tracking** with autocomplete - enables grouping cases by institution
  - Procedure details and surgical specialties (including Trauma, Critical Care, Prehospital)
  - **Multiple anaesthetic techniques** (can select combinations of GA, RA, sedation, LA)
  - **28 regional techniques** (spinal, epidural, nerve blocks, plane blocks)
  - **Regional block documentation:**
    - Technique used (landmark, ultrasound in/out of plane, nerve stimulator)
    - Outcome (successful, partially successful, unsuccessful)
    - Catheter insertion (Y/N)
  - **Airway management with intubation grading:**
    - Direct Laryngoscopy Grade (Cormack-Lehane modified scale: 1, 2a, 2b, 3a, 3b, 4)
    - Video Laryngoscopy (VCI Score): Blade type, POGO score, Tube delivery
    - Based on validated VCI Score system (vciscore.com)
  - **40+ procedures and special techniques** (including thoracostomy, deep extubation)
  - Comprehensive monitoring options (Standard AAGBI)
  - **Enhanced complications tracking** (including unexpected ICU admission and death)
  - **Table 3 supervision levels** (1, 2A, 2B, 3, 4 with detailed descriptions)
  - Supervisor details
  - Learning reflections for CPD

### 🎨 Customizable Interface
- **Light/Dark mode** toggle
- **Three color schemes**: Blue, Red, Green
- Preferences saved across sessions
- Professional medical interface design
- Mobile-optimized with responsive layout

### 🏥 Location & Hospital Management
- **Free text entry** for locations and hospitals
- **Autocomplete** - previously entered values remembered
- **Management interface** in Export tab:
  - View all saved locations and hospitals
  - Delete entries with typos (✕ button on each)
  - Alphabetically sorted lists
  - Safe deletion - doesn't affect existing cases
- **Grouping capability** - analyze cases by hospital/institution
- **Multi-site support** - perfect for locums and rotations

### 📊 Statistics & Analytics
- Total case count tracking
- Breakdown by surgical specialty
- Breakdown by hospital (when using exports)
- ASA grade distribution
- Complication tracking
- Technique frequency analysis
- Regional block outcome tracking

### 💾 Data Export & Backup Options
- **Cloud Backup (Easy & Automatic)**:
  - **Email Backup**: One-click send to yourself for cloud storage
  - **Save to Files**: Direct save to iCloud Drive/Google Drive/Dropbox
  - Both methods work immediately - no setup required!
  - See CLOUD_STORAGE_GUIDE.md for detailed instructions
- **Offline-Ready Exports** (requires JavaScript files - see Installation):
  - **PDF Export**: Professional formatted document suitable for RCoA revalidation
  - **Excel Export**: Multi-sheet workbook with summary statistics and hospital grouping
  - **CSV Export**: Simple spreadsheet format with all fields
- **JSON Export**: Complete backup for data portability and restoration

**⚠️ For offline PDF/Excel exports:** Download required JavaScript files (see OFFLINE_SETUP.md)

### 🔒 Privacy & Security
- **100% Local Storage**: All data stays on your device by default
- **Optional Cloud Backup**: You control where data is synced
- **Offline Capable**: Works without internet connection
- **No Patient Identifiable Information**: Designed for anonymized data only
- **GDPR Compliant**: Full data control and portability
- **Saved lists management**: Remove typos without affecting case history

### 📱 Mobile Optimized
- Responsive design for iPhone and iPad
- Can be installed as a PWA (Add to Home Screen)
- Works like a native app
- Touch-optimized interface
- Location and hospital autocomplete for quick data entry
- Efficient data entry on small screens

## Installation

### ⚠️ CRITICAL FIRST STEP: Download Required Files

**This app requires 3 JavaScript files for PDF and Excel exports to work offline:**

1. **jspdf.umd.min.js** (~200 KB)
2. **jspdf.plugin.autotable.min.js** (~45 KB)  
3. **xlsx.full.min.js** (~800 KB)

**Quick Download:**
See **OFFLINE_SETUP.md** for direct download links and complete instructions.

**File Structure Required:**
```
your-folder/
  ├── index.html (rename anaesthetic-logbook.html to this)
  ├── jspdf.umd.min.js
  ├── jspdf.plugin.autotable.min.js
  └── xlsx.full.min.js
```

**⚠️ Without these files, exports will fail (especially in hospitals with poor WiFi)**

---

### Option 1: Direct Use
1. Download `anaesthetic-logbook.html`
2. Open the file in any modern web browser
3. Start logging cases immediately

### Option 2: Install as PWA (iPhone)
1. Open `anaesthetic-logbook.html` in Safari
2. Tap the Share button (square with arrow)
3. Select "Add to Home Screen"
4. Name it "Anaesthetic Logbook"
5. Tap "Add"
6. The app will now appear on your home screen like a native app

### Option 3: Host on GitHub Pages
1. Create new GitHub repository named `anaesthetic-logbook`
2. **Upload ALL 4 files** (must be in same directory):
   - Rename `anaesthetic-logbook.html` to `index.html`
   - Upload `index.html`
   - Upload `jspdf.umd.min.js`
   - Upload `jspdf.plugin.autotable.min.js`
   - Upload `xlsx.full.min.js`
3. Go to Settings → Pages
4. Select "Deploy from a branch" → "main" branch → Save
5. Your logbook will be available at `https://yourusername.github.io/anaesthetic-logbook/`
6. Add to iPhone home screen (see Option 2)

**⚠️ Critical:** All 4 files must be uploaded together for offline PDF/Excel exports to work!

## Usage

### Adding a New Case
1. Click on the "New Case" tab
2. Fill in the required fields (marked with *):
   - Date, Location, Age, ASA Grade, Procedure
3. **Optional but recommended**: Enter Hospital name
   - Enables grouping cases by institution
   - Perfect for locums or rotation tracking
   - Autocompletes after first use
4. Select anaesthetic technique(s) - **can select multiple** (e.g., GA + RA)
5. For regional blocks, document:
   - Which block(s) performed
   - Technique used (landmark, ultrasound, etc.)
   - Outcome (successful/partially/unsuccessful)
   - Whether catheter was inserted
6. **For intubation cases**, document laryngoscopy views:
   - **Direct laryngoscopy**: Select Cormack-Lehane grade (1-4, with subdivisions)
   - **Video laryngoscopy**: Complete VCI Score (Blade type, POGO %, Tube delivery)
   - Leave blank if not applicable
7. Select relevant procedures, monitoring, and complications
8. Choose supervision level (Table 3: Levels 1, 2A, 2B, 3, 4)
9. Add supervisor name and reflections
10. Click "Save Case"

### Managing Saved Locations & Hospitals
1. Go to "Export" tab
2. Scroll to "Manage Saved Locations" section:
   - View all previously entered locations
   - Click ✕ to delete entries with typos
   - Deletions don't affect existing cases
3. Scroll to "Manage Saved Hospitals" section:
   - View all previously entered hospitals
   - Click ✕ to delete entries with typos
   - Safe deletion - case data unchanged

### Grouping Cases by Hospital
**In Excel Export:**
1. Export to Excel
2. Open in Excel/Google Sheets
3. Use "Sort & Filter" on Hospital column
4. Create pivot tables by hospital
5. Analyze experience across institutions

**Common Use Cases:**
- **Single hospital**: Enter once, reuse via autocomplete
- **Locum work**: Track cases at multiple hospitals
- **Rotation**: Monitor experience at each training site
- **Audit**: Compare practice across institutions

### Customizing Your Experience
1. **Change theme**: Click Dark/Light toggle in header
2. **Change color scheme**: Click color circles (Blue/Red/Green)
3. **Location autocomplete**: Previously entered locations are remembered
4. **Hospital autocomplete**: Previously entered hospitals are remembered
5. Settings persist across sessions

### Viewing Cases
1. Navigate to "My Cases" tab
2. Use search and filters to find specific cases
3. Click on any case to view full details including:
   - All technique and block details
   - Regional block outcomes
   - Complete procedure list
4. Delete cases if needed

### Cloud Backup (Recommended)
1. Go to "Export" tab
2. **Option A - Email Backup** (Simplest):
   - Click "📧 Email Backup"
   - Email opens with backup file
   - Send to yourself
   - Automatic cloud storage in Gmail/Outlook
   - Takes 30 seconds, do weekly
3. **Option B - Save to Files** (Best for Mobile):
   - Click "💾 Save to Files"
   - Choose iCloud Drive (iOS) or Google Drive (Android)
   - File syncs automatically
   - Perfect for automatic backup
4. **Set weekly reminder**: Sunday 8pm to backup!

See **CLOUD_STORAGE_GUIDE.md** for detailed platform-specific instructions.

### Exporting Data
1. Go to the "Export" tab
2. Choose your export format:
   - **PDF**: Best for RCoA submission and revalidation
   - **Excel**: Best for detailed analysis and statistics (includes regional block breakdown)
   - **CSV**: Compatible with most spreadsheet software
   - **JSON**: For backup and data portability

### Statistics
1. Click on "Statistics" tab
2. View breakdowns by:
   - Total cases
   - Anaesthetic technique
   - Surgical specialty
   - ASA grade
   - Complications

## Technical Details

### Technologies Used
- HTML5
- CSS3 (with custom properties for theming)
- Vanilla JavaScript (no framework dependencies)
- Local Storage API
- External Libraries:
  - jsPDF (PDF generation)
  - jsPDF-AutoTable (PDF tables)
  - SheetJS (Excel generation)

### Browser Compatibility
- ✅ Chrome/Edge (latest)
- ✅ Safari (iOS 12+)
- ✅ Firefox (latest)
- ⚠️ Internet Explorer (not supported)

### Data Storage
- All data stored in browser's localStorage by default
- Typical storage limit: 5-10MB (sufficient for thousands of cases)
- Data persists between sessions
- Survives browser restarts
- **Safari**: Reliable but can be cleared with browser data - **regular backups essential**
- **Cloud backup options**:
  - Manual export to Google Drive/Dropbox/Box (recommended)
  - Optional automatic sync with OAuth setup (see CLOUD_STORAGE_GUIDE.md)

### Safari-Specific Notes
✅ **Works reliably** on Safari (iOS and Mac)
⚠️ **Data can be lost** if you:
- Clear Safari browsing data/cache
- Delete website data in Settings
- Use Private Browsing mode (won't save)
- Uninstall PWA from home screen

📱 **Best practice for Safari users**:
1. Add to Home Screen for best experience
2. Export to JSON weekly (set phone reminder)
3. Upload backups to iCloud Drive or cloud storage
4. Never clear browser data without backing up first

💡 **Pro tip**: Each case is ~1-2KB. You can store 1,000+ cases easily.

## Data Privacy & Compliance

### Important Notes
⚠️ **This is a prototype application**. For full GMC revalidation compliance, you should:

1. **Never store patient-identifiable information**
   - Do not use patient names, NHS numbers, or hospital numbers
   - Use anonymized data only
   - Hospital field is for institution name only (e.g., "Royal Infirmary")

2. **Regular Backups are ESSENTIAL**
   - **Recommended**: Email Backup weekly (takes 30 seconds)
   - **Or**: Save to Files → iCloud/Google Drive weekly (takes 10 seconds)
   - **Best practice**: Use both methods for redundancy
   - **Before revalidation**: Export all formats (PDF, Excel, JSON)
   - Set phone/calendar reminders for weekly backups
   - See CLOUD_STORAGE_GUIDE.md for detailed backup strategies

3. **Safari Users - Extra Caution**
   - Data stored in browser can be cleared accidentally
   - Private browsing mode doesn't save data
   - Always maintain current cloud backups
   - Test: Save case → Close Safari → Reopen → Check case still there

4. **Location & Hospital Data**
   - Saved locations and hospitals stored separately
   - Can delete typos from autocomplete lists safely
   - Deleting from lists doesn't affect case records
   - Export includes all location and hospital data

5. **Data Protection**
   - This app stores data locally on your device by default
   - Optional cloud sync puts data in YOUR cloud account (you control it)
   - No third-party access to your data
   - Export and delete data anytime
   - Hospital field for institution tracking, not patient location

6. **Production Use**
   - For professional use, consider:
     - Implementing secure backend storage
     - Adding encryption
     - GDPR/Data Protection Act compliance measures
     - NHS Digital compliance
     - Audit trails
   - Or use with robust backup procedures

### Cloud Storage Options
**Working solutions (no setup required):**

**Email Backup** - Simplest method:
- One-click send backup to yourself
- Automatic cloud storage in Gmail/Outlook
- Searchable email archive
- Easy sharing with supervisors
- Works on all devices

**Save to Files** - Best for mobile:
- Direct save to iCloud Drive (iOS)
- Direct save to Google Drive (Android)  
- Automatic cloud synchronization
- Native OS integration
- Works offline, syncs when connected

See **CLOUD_STORAGE_GUIDE.md** for:
- Step-by-step instructions for your device
- Platform-specific tips (iOS/Android/Desktop)
- Backup strategies and schedules
- Security and privacy information
- Troubleshooting help

### Hospital Grouping Benefits
- **Multi-site tracking**: Perfect for locums and rotations
- **Institutional analysis**: Compare your practice across hospitals
- **Audit capability**: Group cases by institution in Excel
- **Career portfolio**: Show breadth of experience
- **No patient data**: Only records institution name

## Airway Management Grading

### Cormack-Lehane Grade (Direct Laryngoscopy)
Modified scale with six grades:
- **Grade 1**: Full view of glottis
- **Grade 2a**: Partial view of glottis
- **Grade 2b**: Only arytenoids visible
- **Grade 3a**: Only epiglottis visible (can be lifted)
- **Grade 3b**: Only epiglottis visible (cannot be lifted)
- **Grade 4**: No glottic structures visible

### VCI Score (Video Laryngoscopy)
Three-component validated scoring system:

**1. Blade Type** (categorized):
- Macintosh-type: CMAC Macintosh, Glidescope Macintosh, McGrath Macintosh
- Hyperangulated: CMAC D blade, Glidescope original, McGrath X blade
- Channelled: Airtraq, Kingvision
- Other: Miller blades, specialty blades

**2. POGO Score**:
- Percentage of Glottic Opening (0%, 25%, 50%, 75%, 100%)
- Recorded at moment of intubation attempt

**3. Tube Delivery**:
- Straightforward, no adjuncts
- As per manufacturer's recommendation
- Needed bougie/Magill's/flexible scope
- Failed delivery

**Reference**: Based on VCI Score Project (vciscore.com) and British Journal of Anaesthesia publication (2025)

**Use Cases**:
- Difficult airway documentation
- Video laryngoscopy training
- Quality improvement and research
- DOPS/ACAT evidence

## Regional Techniques Supported

### Neuraxial
- Spinal
- Epidural (Lumbar, Thoracic)
- Combined Spinal-Epidural (CSE)
- Epidural Top-up
- Caudal

### Upper Limb
- Brachial Plexus (Interscalene, Supraclavicular, Infraclavicular)
- Axillary Nerve
- Ulnar

### Lower Limb
- Femoral
- Adductor Canal Block
- Fascia Iliaca
- Sciatic
- Popliteal
- Ankle
- Femoral-Sciatic Combined

### Truncal Blocks
- TAP (Transversus Abdominis Plane)
- Erector Spinae Plane (ESP)
- Quadratus Lumborum
- Rectus Sheath
- Paravertebral
- Intercostal

### Other
- Cervical Plexus (Deep, Superficial)
- Penile Block
- Eye Subtenon

### Regional Block Documentation
For each block, you can record:
- **Technique**: Landmark, Ultrasound (in-plane/out-of-plane), Nerve Stimulator, or combinations
- **Outcome**: Successful, Partially Successful, Unsuccessful, or No value
- **Catheter**: Yes/No

## Procedures & Techniques Supported

### Airway Management
- RSI (Rapid Sequence Induction)
- Video Laryngoscopy
- Fibreoptic Intubation (Awake/Asleep)
- DLT (Double Lumen Tube)
- Nasal Intubation
- Front of Neck Access

### IV Techniques
- TIVA
- TCI (Target Controlled Infusion)
- Inhalation Induction

### Vascular Access
- Central Lines (Jugular, Subclavian, Femoral, Other)
- Arterial Lines
- Vascath

### Advanced Procedures
- Cardiopulmonary Bypass (CPB)
- Deep Hypothermic Circulatory Arrest (DHCA)
- Massive Transfusion
- Bronchoscopy
- Chest Drains (Seldinger, Surgical)
- Thoracotomy
- **Thoracostomy**
- Percutaneous Tracheostomy
- **Deep Extubation**

### Oxygenation Techniques
- THRIVE
- Apnoeic Oxygenation
- Injector Ventilation

### Other
- Prone Positioning
- Lumbar Puncture
- Ascitic Drain
- Brain Stem Testing
- CPET (Cardiopulmonary Exercise Testing)

## Surgical Specialties

- General Surgery
- Orthopaedics
- **Trauma**
- Urology
- Gynaecology
- Obstetrics
- ENT
- Ophthalmology
- Plastic Surgery
- Neurosurgery
- Cardiothoracic
- Vascular
- Paediatric Surgery
- Dental
- Maxillofacial
- **Critical Care**
- Pain Medicine
- Radiology
- **Prehospital**

## Screenshots

*Add screenshots here of the main interface, case entry form, and export options*

## Roadmap

### Completed in v2.2 ✅
- [x] Intubation grading system
- [x] Cormack-Lehane modified scale
- [x] VCI Score for videolaryngoscopy (official 3-component system)
- [x] Comprehensive airway documentation

### Completed in v2.1 ✅
- [x] Hospital field with autocomplete
- [x] Hospital management (add/delete from saved list)
- [x] Hospital grouping in exports
- [x] **Working cloud backup** (Email + Save to Files)
- [x] Removed non-functional OAuth placeholders

### Completed in v2.0 ✅
- [x] Light/Dark theme with color schemes
- [x] Location autocomplete with management
- [x] Multiple anaesthetic techniques selection
- [x] Regional block technique, outcome, and catheter tracking
- [x] Table 3 supervision levels
- [x] Enhanced complications tracking
- [x] Additional procedures (thoracostomy, deep extubation)

### Future Enhancements
- [ ] Weekly backup reminder notifications (in-app)
- [ ] Google Sheets integration (direct sync to spreadsheet)
- [ ] Advanced analytics and charts
  - Cases by hospital over time
  - Regional block success rates by technique
  - Complication trends
  - **Airway difficulty analysis** (C-L grade distribution, VCI score trends)
  - **Failed intubation tracking**
- [ ] Filter cases by hospital in the app
- [ ] Hospital-specific statistics view
- [ ] **Airway statistics dashboard**:
  - C-L grade distribution
  - VCI blade preferences
  - POGO score averages
  - Tube delivery difficulty rates
- [ ] VCI score calculator within app
- [ ] Import from CSV/Excel
- [ ] Customizable case templates
- [ ] Photo attachments for learning documentation
- [ ] Voice-to-text for reflections
- [ ] Automated RCoA report generation
- [ ] Colleague verification/sign-off workflow
- [ ] Additional export formats (Word, PowerPoint)
- [ ] Browser extension for Chrome/Edge sync
- [ ] QR code export/import for offline transfer
- [ ] Offline sync queue (save cases offline, sync when online)
- [ ] Multi-user support for departments
- [ ] Case sharing for teaching/audit
- [ ] Search by hospital/location/airway grade
- [ ] Bulk edit hospital names (for mergers/rebranding)
- [ ] Difficult airway alerts/flagging system

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development Setup
1. Clone the repository
2. Open `anaesthetic-logbook.html` in your browser
3. Make changes
4. Test thoroughly
5. Submit PR

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- Based on RCoA Lifelong Learning Platform requirements
- Designed for GMC revalidation compliance
- Inspired by the needs of anaesthetists in training and practice

## Disclaimer

**This software is provided "as is" without warranty of any kind.** 

- This is an educational and productivity tool
- Not certified for official medical record keeping
- Users are responsible for ensuring compliance with local regulations
- Always maintain official hospital records as required
- Regular data backups are the user's responsibility
- The developers are not liable for any data loss or compliance issues

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing issues for solutions
- Contribute improvements via Pull Requests

## Version History

### v2.2.0 (February 2026)
- **Intubation Grading System**:
  - Direct Laryngoscopy Grade using Cormack-Lehane modified scale (1, 2a, 2b, 3a, 3b, 4)
  - Video Laryngoscopy using official VCI Score system (Blade, POGO, Tube Delivery)
  - Based on validated VCI Score from vciscore.com (BJA 2025)
  - Optional fields - complete only if intubation performed
- **Enhanced Airway Documentation**:
  - Three-component VCI scoring (blade type, POGO percentage, tube delivery)
  - Categorized blade selection (Macintosh-type, Hyperangulated, Channelled)
  - Support for research and audit data collection
  - All airway grades included in exports
- **Improved Data Exports**:
  - Separate CSV columns for C-L grade and VCI components
  - Comprehensive airway data in all export formats
- **iOS Critical Fixes**:
  - Input zoom prevention (16px fonts)
  - iPhone notch support (safe-area-insets)
  - Swipe-back prevention (overscroll-behavior)
  - 7-day backup warning system
  - PII disclaimer on first load
- **Offline Capability**:
  - Changed to local JavaScript files (no CDN dependency)
  - Works in hospitals with poor WiFi
  - Requires downloading 3 JS files (see OFFLINE_SETUP.md)
  - PDF and Excel exports work offline

### v2.1.0 (January 2026)
- **Hospital Field**: Added dedicated hospital field for institution tracking
  - Free text with autocomplete
  - Enables grouping cases by hospital in Excel
  - Perfect for locums and rotation tracking
- **Working Cloud Backup Solutions**:
  - Email Backup button - send backup to yourself in 30 seconds
  - Save to Files button - direct save to iCloud/Google Drive
  - Replaced non-functional OAuth placeholders with working solutions
  - No setup required - works immediately
- **Enhanced Data Management**:
  - "Manage Saved Hospitals" section in Export tab
  - Delete hospital entries with typos (safe - doesn't affect cases)
  - Improved location management interface
  - Both lists alphabetically sorted
- **Improved Case Display**:
  - Hospital shown in case list (🏥 icon)
  - Hospital displayed in case detail view
  - All exports include hospital column
- **Better Visual Organization**:
  - Specialty icon changed to 🔬 (was 🏥)
  - Hospital has dedicated 🏥 icon
  - Clearer visual distinction between fields

### v2.0.0 (January 2026)
- **Theme System**: Light/Dark mode with Blue/Red/Green color schemes
- **Location Tracking**: Autocomplete for previously entered locations
- **Multiple Techniques**: Can now select multiple anaesthetic techniques simultaneously
- **Enhanced Regional Blocks**:
  - Added technique documentation (landmark, US in/out plane, nerve stimulator)
  - Added outcome tracking (successful/partially/unsuccessful)
  - Added catheter insertion field (Y/N)
  - Removed Cervical Plexus Combined
- **Updated Supervision**: Table 3 levels (1, 2A, 2B, 3, 4) with detailed descriptions
- **New Specialties**: Trauma, Critical Care, Prehospital
- **New Complications**: Unexpected critical care admission, Death
- **New Procedures**: Thoracostomy, Deep extubation
- **Monitoring**: Changed to "Standard AAGBI"
- **Cloud Storage UI**: Interface for Google Drive, Dropbox, Box sync (OAuth setup required)
- **Improved Exports**: All formats updated with new fields
- **Enhanced Mobile UI**: Better responsive design for theme controls
- **Data Migration**: Automatic conversion of old case format to new structure

### v1.0.0 (January 2026)
- Initial release
- Full RCoA logbook fields
- 30+ regional techniques
- 38+ procedures
- PDF, Excel, CSV, JSON export
- Statistics dashboard
- Mobile-optimized PWA
- Offline capability

---

**Made with ❤️ for anaesthetists, by anaesthetists**

*Remember: Patient safety first. This tool is to support your learning and revalidation, not replace proper clinical documentation.*
