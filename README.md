# Anaesthetic Logbook App

A comprehensive Progressive Web App (PWA) for anaesthetists to log and manage their clinical cases in accordance with RCoA (Royal College of Anaesthetists) guidelines for GMC revalidation.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## Features

### 📋 Complete Case Logging
- Full RCoA logbook fields including:
  - Patient demographics (age, sex, ASA grade)
  - Procedure details and surgical specialties
  - Anaesthetic techniques (GA, RA, sedation, LA)
  - 30+ regional techniques (spinal, epidural, nerve blocks, plane blocks)
  - 38+ procedures and special techniques
  - Comprehensive monitoring options
  - Airway management details
  - Complications and critical events tracking
  - Supervision levels and supervisor details
  - Learning reflections for CPD

### 📊 Statistics & Analytics
- Total case count tracking
- Breakdown by surgical specialty
- ASA grade distribution
- Complication tracking
- Technique frequency analysis

### 💾 Data Export Options
- **PDF Export**: Professional formatted document suitable for RCoA revalidation
- **Excel Export**: Multi-sheet workbook with summary statistics and detailed case data
- **CSV Export**: Simple spreadsheet format for further analysis
- **JSON Export**: Complete backup for data portability

### 🔒 Privacy & Security
- **100% Local Storage**: All data stays on your device
- **No Cloud Upload**: Complete data privacy
- **Offline Capable**: Works without internet connection
- **No Patient Identifiable Information**: Designed for anonymized data only

### 📱 Mobile Optimized
- Responsive design for iPhone and iPad
- Can be installed as a PWA (Add to Home Screen)
- Works like a native app
- Touch-optimized interface

## Installation

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
1. Fork this repository
2. Go to Settings → Pages
3. Select "Deploy from a branch"
4. Choose "main" branch
5. Your logbook will be available at `https://yourusername.github.io/anaesthetic-logbook/`

## Usage

### Adding a New Case
1. Click on the "New Case" tab
2. Fill in the required fields (marked with *)
3. Select relevant techniques, procedures, and monitoring
4. Add any complications or reflections
5. Click "Save Case"

### Viewing Cases
1. Navigate to "My Cases" tab
2. Use search and filters to find specific cases
3. Click on any case to view full details
4. Delete cases if needed

### Exporting Data
1. Go to the "Export" tab
2. Choose your export format:
   - **PDF**: Best for RCoA submission and revalidation
   - **Excel**: Best for detailed analysis and statistics
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
- All data stored in browser's localStorage
- Typical storage limit: 5-10MB (sufficient for thousands of cases)
- Data persists between sessions
- Survives browser restarts

## Data Privacy & Compliance

### Important Notes
⚠️ **This is a prototype application**. For full GMC revalidation compliance, you should:

1. **Never store patient-identifiable information**
   - Do not use patient names, NHS numbers, or hospital numbers
   - Use anonymized data only

2. **Regular Backups**
   - Export your data regularly using JSON export
   - Store backups securely

3. **Data Protection**
   - This app stores data locally on your device only
   - If you clear browser data, you will lose your cases
   - No cloud backup is provided by default

4. **Production Use**
   - For professional use, consider:
     - Implementing secure backend storage
     - Adding encryption
     - GDPR/Data Protection Act compliance measures
     - NHS Digital compliance
     - Audit trails

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
- Cervical Plexus (Combined, Deep, Superficial)
- Penile Block
- Eye Subtenon

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
- Percutaneous Tracheostomy

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
- Critical Care
- Pain Medicine
- Radiology
- Trauma

## Screenshots

*Add screenshots here of the main interface, case entry form, and export options*

## Roadmap

### Future Enhancements
- [ ] Cloud sync option (with encryption)
- [ ] Multi-device synchronization
- [ ] Advanced analytics and charts
- [ ] Import from CSV/Excel
- [ ] Customizable templates
- [ ] Photo attachments for learning points
- [ ] Voice-to-text for reflections
- [ ] Integration with hospital systems (with appropriate permissions)
- [ ] Automated RCoA report generation
- [ ] Colleague verification/sign-off features

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
