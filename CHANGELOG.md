# Changelog

All notable changes to the Anaesthetic Logbook project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.2.0] - 2026-02-01

### Added
- **Intubation Grading System**:
  - **Direct Laryngoscopy Grade (Cormack-Lehane)**: Modified scale with grades 1, 2a, 2b, 3a, 3b, 4
  - **VCI Score for Videolaryngoscopy**: Official three-component scoring system
    - VCI Blade Type: Categorized dropdown (Macintosh-type, Hyperangulated, Channelled, Other)
    - VCI POGO Score: Percentage of Glottic Opening (0%, 25%, 50%, 75%, 100%)
    - VCI Tube Delivery: Documentation of intubation ease (straightforward to failed)
  - Based on validated VCI Score system (vciscore.com, BJA 2025)
- **Enhanced Airway Documentation**:
  - All three VCI components displayed in case details
  - Separate CSV export columns for VCI Blade, POGO, and Tube Delivery
  - Support for both direct laryngoscopy and videolaryngoscopy grading
  - Optional fields - only complete if intubation performed
- **iOS Critical Fixes**:
  - Input zoom prevention: All form inputs now use 16px font (prevents iOS auto-zoom)
  - iPhone notch support: Safe-area-insets for header and body
  - Swipe-back prevention: overscroll-behavior prevents accidental navigation
  - 7-day backup warning system: Red banner appears if no backup in 7+ days
  - PII disclaimer modal: Privacy warning on first app load
  - iOS-optimized viewport: viewport-fit=cover for full-screen experience
- **Offline Capability**:
  - Local JavaScript files (no CDN dependency)
  - PDF and Excel exports work without internet
  - Requires 3 JS files: jspdf.umd.min.js, jspdf.plugin.autotable.min.js, xlsx.full.min.js
  - See OFFLINE_SETUP.md for download instructions

### Changed
- **Airway Management Section**: Expanded with intubation grading fields
- **Case Detail Modal**: Now displays Cormack-Lehane grade and VCI components separately
- **Export Formats**: CSV includes new airway grading columns
- **Script Tags**: Changed from CDN URLs to local file paths for offline reliability
- **Viewport Meta**: Removed user-scalable=no for accessibility compliance

### Technical
- VCI scoring matches official VCI Project implementation
- Backward compatible with old cases
- Three separate data fields for VCI components (blade, POGO, delivery)
- Legacy `videoLaryngoscopyGrade` field preserved for old data
- Input font-size: 16px minimum (iOS zoom prevention)
- CSS safe-area-inset support for notch devices
- Backup timestamp system tracks last export date
- PII disclaimer stored in localStorage (shows once)

## [2.1.0] - 2026-01-31

### Added
- **Hospital Field**: New dedicated field for recording hospital/institution name
  - Free text input with autocomplete functionality
  - Automatically saves hospitals to remembered list
  - Enables grouping and analyzing cases by institution
- **Hospital Management Interface** in Export tab:
  - "Manage Saved Hospitals" section
  - View all previously entered hospitals
  - Delete hospitals with typos using ✕ button
  - Alphabetically sorted list
  - Safe deletion (doesn't affect existing case records)
- **Hospital Display** throughout app:
  - Shows in case list with 🏥 icon
  - Displayed in case detail modal
  - Included in all export formats (PDF, Excel, CSV, JSON)
- **Enhanced Export Functionality**:
  - Hospital column in CSV export
  - Hospital field in Excel export for filtering/grouping
  - Hospital data in PDF case details
- **Working Cloud Backup Solutions**:
  - **Email Backup button**: One-click send backup to yourself
  - **Save to Files button**: Direct save to iCloud Drive/Google Drive/Dropbox
  - Uses native OS cloud integration (no setup required)
  - Web Share API support for mobile devices
  - File System Access API for desktop
  - Comprehensive CLOUD_STORAGE_GUIDE.md with platform-specific instructions

### Changed
- **Visual Icon Updates**:
  - Specialty changed from 🏥 to 🔬 for clarity
  - Hospital now uses 🏥 icon
  - Better visual distinction between fields
- **Location Label**: Clarified as "Location (where case was performed)"
- **Export Tab Organization**: 
  - Separate sections for Location and Hospital management
  - New "Cloud Backup (Working Solutions)" section
  - Removed non-functional OAuth placeholders
- **Cloud Storage Approach**:
  - Replaced OAuth integration UI with working solutions
  - Simplified user experience
  - No developer setup required

### Removed
- **OAuth Cloud Storage Buttons**: Removed Google Drive, Dropbox, Box OAuth buttons
  - Required complex developer setup that 99% of users couldn't complete
  - Replaced with working Email and File backup solutions
- **Cloud Sync Configuration**: Removed non-functional sync status and settings
- **Misleading Features**: Removed placeholder code that suggested features that didn't work

### Fixed
- Icon overlap between specialty and hospital fields
- Improved visual hierarchy in case displays
- Cloud backup actually works now (not just placeholders)

## [2.0.0] - 2026-01-30

### Added
- **Theme System**: Light/Dark mode toggle with persistent preferences
- **Color Schemes**: Blue (default), Red, and Green color options
- **Location Field**: Required location field with autocomplete for previously entered locations
- **Multiple Anaesthetic Techniques**: Changed from single radio selection to multiple checkbox selection
- **Regional Block Documentation**:
  - Technique selection (Landmark, Ultrasound In-Plane, Ultrasound Out-of-Plane, US + Nerve Stimulator, Nerve Stimulator only)
  - Outcome tracking (Successful, Partially Successful, Unsuccessful, No value)
  - Catheter insertion field (Yes/No)
- **New Surgical Specialties**: Trauma, Critical Care, Prehospital
- **New Complications**: Unexpected Critical Care Admission, Death
- **New Procedures**: Thoracostomy, Deep Extubation
- **Cloud Storage Integration UI**:
  - Interface for Google Drive, Dropbox, and Box
  - Connection status display
  - Manual and automatic sync options
  - Framework for OAuth implementation
- **Comprehensive Cloud Storage Guide** (CLOUD_STORAGE_GUIDE.md)
- **Safari-specific documentation** about data storage and reliability

### Changed
- **Supervision Levels**: Updated to Table 3 format with 5 levels (1, 2A, 2B, 3, 4) with detailed descriptions
- **Monitoring**: "Standard monitoring" changed to "Standard AAGBI"
- **Primary Technique**: Renamed to "Technique" and allows multiple selections
- **Header Layout**: Reorganized to include theme controls
- **Export Formats**: All exports (PDF, Excel, CSV) updated to include new fields
- **Statistics Calculations**: Updated to handle multiple technique selections
- **Case Display**: Now shows location and multiple techniques
- **Mobile Responsiveness**: Improved responsive design for theme controls

### Removed
- **Cervical Plexus Combined**: Removed from regional techniques list (kept Deep and Superficial)
- Old supervision level options (replaced with Table 3 format)

### Fixed
- **Data Migration**: Automatic conversion of old `primaryTechnique` field to new `techniques` array
- **Backward Compatibility**: All old cases display correctly with new field structure
- **Export Compatibility**: Legacy data exports properly in all formats

### Security
- Added detailed Safari data storage warnings
- Enhanced backup recommendations
- Cloud storage privacy documentation
- Multiple backup location strategies

## [1.0.0] - 2026-01-30

### Added
- Initial release of Anaesthetic Logbook
- Complete RCoA logbook field support
- Patient demographics tracking (age, sex, ASA grade)
- Procedure and surgical specialty logging
- Anaesthetic technique selection (GA, RA, Sedation, LA)
- 30+ regional anaesthetic techniques
- 38+ procedures and special techniques
- Comprehensive monitoring options
- Complications and critical events tracking
- Supervision level recording
- CPD reflections and learning points
- Search and filter functionality
- Case detail viewing
- Statistics dashboard
- Export functionality (PDF, Excel, CSV, JSON)
- Import functionality for JSON backups
- Local storage for complete data privacy
- Offline capability (PWA)
- Mobile-optimized responsive design
- iOS PWA support (Add to Home Screen)
- Professional medical interface design

### Security
- All data stored locally in browser localStorage
- No cloud upload or external data transmission
- Privacy-first design for GDPR compliance
- No patient identifiable information fields

## [Unreleased]

### Planned Features
- Weekly backup reminder notifications (in-app)
- Google Sheets integration (direct sync to spreadsheet)
- Advanced analytics and charts
  - Cases by hospital over time
  - Regional block success rates
  - Complication trends
  - Airway difficulty analysis (C-L grades, VCI scores)
- Filter cases by hospital in the app
- Hospital-specific statistics view
- Import from CSV/Excel
- Customizable case templates
- Photo attachments for learning documentation
- Voice-to-text for reflections
- Automated RCoA report generation
- Colleague verification/sign-off workflow
- Additional export formats (Word, PowerPoint)
- Browser extension for Chrome/Edge sync
- QR code export/import for offline transfer
- Offline sync queue (save cases offline, sync when online)
- Multi-user support for departments
- Case sharing for teaching/audit
- Search by hospital/location
- Bulk edit hospital names (for mergers/rebranding)
- VCI score calculator within app
- Airway difficulty statistics dashboard

---

## Version Number Scheme

- **Major version** (X.0.0): Significant changes, major new features, or breaking changes
- **Minor version** (2.X.0): New features, enhancements, no breaking changes
- **Patch version** (2.2.X): Bug fixes, minor improvements

## Dates

Dates are formatted as YYYY-MM-DD (ISO 8601 format).

## Categories

- **Added**: New features
- **Changed**: Changes to existing functionality
- **Deprecated**: Soon-to-be removed features
- **Removed**: Removed features
- **Fixed**: Bug fixes
- **Security**: Security improvements or fixes
- **Technical**: Implementation details for developers

### Added
- **Hospital Field**: New dedicated field for recording hospital/institution name
  - Free text input with autocomplete functionality
  - Automatically saves hospitals to remembered list
  - Enables grouping and analyzing cases by institution
- **Hospital Management Interface** in Export tab:
  - "Manage Saved Hospitals" section
  - View all previously entered hospitals
  - Delete hospitals with typos using ✕ button
  - Alphabetically sorted list
  - Safe deletion (doesn't affect existing case records)
- **Hospital Display** throughout app:
  - Shows in case list with 🏥 icon
  - Displayed in case detail modal
  - Included in all export formats (PDF, Excel, CSV, JSON)
- **Enhanced Export Functionality**:
  - Hospital column in CSV export
  - Hospital field in Excel export for filtering/grouping
  - Hospital data in PDF case details
- **Working Cloud Backup Solutions**:
  - **Email Backup button**: One-click send backup to yourself
  - **Save to Files button**: Direct save to iCloud Drive/Google Drive/Dropbox
  - Uses native OS cloud integration (no setup required)
  - Web Share API support for mobile devices
  - File System Access API for desktop
  - Comprehensive CLOUD_STORAGE_GUIDE.md with platform-specific instructions

### Changed
- **Visual Icon Updates**:
  - Specialty changed from 🏥 to 🔬 for clarity
  - Hospital now uses 🏥 icon
  - Better visual distinction between fields
- **Location Label**: Clarified as "Location (where case was performed)"
- **Export Tab Organization**: 
  - Separate sections for Location and Hospital management
  - New "Cloud Backup (Working Solutions)" section
  - Removed non-functional OAuth placeholders
- **Cloud Storage Approach**:
  - Replaced OAuth integration UI with working solutions
  - Simplified user experience
  - No developer setup required

### Removed
- **OAuth Cloud Storage Buttons**: Removed Google Drive, Dropbox, Box OAuth buttons
  - Required complex developer setup that 99% of users couldn't complete
  - Replaced with working Email and File backup solutions
- **Cloud Sync Configuration**: Removed non-functional sync status and settings
- **Misleading Features**: Removed placeholder code that suggested features that didn't work

### Fixed
- Icon overlap between specialty and hospital fields
- Improved visual hierarchy in case displays
- Cloud backup actually works now (not just placeholders)

## [2.0.0] - 2026-01-30

### Added
- **Theme System**: Light/Dark mode toggle with persistent preferences
- **Color Schemes**: Blue (default), Red, and Green color options
- **Location Field**: Required location field with autocomplete for previously entered locations
- **Multiple Anaesthetic Techniques**: Changed from single radio selection to multiple checkbox selection
- **Regional Block Documentation**:
  - Technique selection (Landmark, Ultrasound In-Plane, Ultrasound Out-of-Plane, US + Nerve Stimulator, Nerve Stimulator only)
  - Outcome tracking (Successful, Partially Successful, Unsuccessful, No value)
  - Catheter insertion field (Yes/No)
- **New Surgical Specialties**: Trauma, Critical Care, Prehospital
- **New Complications**: Unexpected Critical Care Admission, Death
- **New Procedures**: Thoracostomy, Deep Extubation
- **Cloud Storage Integration UI**:
  - Interface for Google Drive, Dropbox, and Box
  - Connection status display
  - Manual and automatic sync options
  - Framework for OAuth implementation
- **Comprehensive Cloud Storage Guide** (CLOUD_STORAGE_GUIDE.md)
- **Safari-specific documentation** about data storage and reliability

### Changed
- **Supervision Levels**: Updated to Table 3 format with 5 levels (1, 2A, 2B, 3, 4) with detailed descriptions
- **Monitoring**: "Standard monitoring" changed to "Standard AAGBI"
- **Primary Technique**: Renamed to "Technique" and allows multiple selections
- **Header Layout**: Reorganized to include theme controls
- **Export Formats**: All exports (PDF, Excel, CSV) updated to include new fields
- **Statistics Calculations**: Updated to handle multiple technique selections
- **Case Display**: Now shows location and multiple techniques
- **Mobile Responsiveness**: Improved responsive design for theme controls

### Removed
- **Cervical Plexus Combined**: Removed from regional techniques list (kept Deep and Superficial)
- Old supervision level options (replaced with Table 3 format)

### Fixed
- **Data Migration**: Automatic conversion of old `primaryTechnique` field to new `techniques` array
- **Backward Compatibility**: All old cases display correctly with new field structure
- **Export Compatibility**: Legacy data exports properly in all formats

### Security
- Added detailed Safari data storage warnings
- Enhanced backup recommendations
- Cloud storage privacy documentation
- Multiple backup location strategies

## [1.0.0] - 2026-01-30

### Added
- Initial release of Anaesthetic Logbook
- Complete RCoA logbook field support
- Patient demographics tracking (age, sex, ASA grade)
- Procedure and surgical specialty logging
- Anaesthetic technique selection (GA, RA, Sedation, LA)
- 30+ regional anaesthetic techniques
- 38+ procedures and special techniques
- Comprehensive monitoring options
- Complications and critical events tracking
- Supervision level recording
- CPD reflections and learning points
- Search and filter functionality
- Case detail viewing
- Statistics dashboard
- Export functionality (PDF, Excel, CSV, JSON)
- Import functionality for JSON backups
- Local storage for complete data privacy
- Offline capability (PWA)
- Mobile-optimized responsive design
- iOS PWA support (Add to Home Screen)
- Professional medical interface design

### Security
- All data stored locally in browser localStorage
- No cloud upload or external data transmission
- Privacy-first design for GDPR compliance
- No patient identifiable information fields

## [Unreleased]

### Planned Features
- Working OAuth implementation for cloud storage
- Weekly backup reminder notifications
- Advanced analytics with charts and graphs
- Import from CSV/Excel
- Customizable case templates
- Photo attachments for learning documentation
- Voice-to-text for reflections
- Automated RCoA report generation
- Colleague verification/sign-off workflow
- Additional export formats (Word, PowerPoint)
- Integration capabilities with hospital systems
- Offline sync queue
- Multi-user support

---

## Version Number Scheme

- **Major version** (X.0.0): Significant changes, major new features, or breaking changes
- **Minor version** (2.X.0): New features, enhancements, no breaking changes
- **Patch version** (2.0.X): Bug fixes, minor improvements

## Dates

Dates are formatted as YYYY-MM-DD (ISO 8601 format).

## Categories

- **Added**: New features
- **Changed**: Changes to existing functionality
- **Deprecated**: Soon-to-be removed features
- **Removed**: Removed features
- **Fixed**: Bug fixes
- **Security**: Security improvements or fixes
