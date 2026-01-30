# Changelog

All notable changes to the Anaesthetic Logbook project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
