# AidHarmony - Transparent Charity Management Platform

AidHarmony is a secure, responsive, and audit-verifiable charity management platform designed using Flutter. It is tailored for mobile and web responsive environments, supporting dynamic localization toggles, compliance audits, and milestone-based fundraising trackers.

---

## 🌟 Core Feature Suite

1. **Role-Based Onboarding & Dashboards**:
   - **Charity Organizations**: Upload legal NGO credentials, draft multi-modal campaigns, upload compliance evidence, and audit pledges.
   - **Donors**: Geolocation proximity campaign finder, material goods pledge selector, and PDF receipt visualizer.
   - **Volunteers**: Professional tag matching profile chips and matching assignment trackers.
   - **Compliance Administrators**: Ingest onboarding NGOs, audit milestone documents/images, approve unlocks, or flag weak evidence.
2. **Multi-Modal Campaigns**: Campaigns support target cash limits, checked checklists for material items, and volunteer skill tags.
3. **Double-Entry Public ledger**: Every transaction, pledge, compliance approval, and flag compiles a secure public ledger audit trail with visual graphing.
4. **Physical PDF Receipts**: Donors and volunteers can download, save, or print formatted cryptographic invoices complete with ledger hashes and key signatures.
5. **Amharic & English Localization**: A global language context manager toggles the app instantly.

---

## 🔑 Demo Access Credentials

To ease evaluation, the database service is pre-seeded with sample profiles and data. You can log in using these details or select the Quick Login buttons on the Auth portal:

| Role | Username / Email | Password |
| :--- | :--- | :--- |
| **System Administrator** | `admin@aidharmony.org` | *Any value (e.g. `admin123`)* |
| **Verified NGO** | `hope@charity.org` | *Any value (e.g. `hope123`)* |
| **Unverified NGO** | `green@charity.org` | *Any value (e.g. `green123`)* |
| **Donor Entity** | `donor@gmail.com` | *Any value (e.g. `donor123`)* |
| **Volunteer Specialist** | `volunteer@gmail.com` | *Any value (e.g. `volunteer123`)* |

---

## 🚀 Setting Up the Application

### 1. Prerequisites
- **Flutter SDK**: Stable channel (v3.0.0+)
- **Dart SDK**: v3.0.0+
- **IDE**: Android Studio, VS Code, or Cursor.

### 2. Configure Dependencies
Open a command prompt at the root directory of the project and run:
```bash
flutter pub get
```

### 3. Run the Development Server
To launch the application locally, run:
```bash
# Run web client
flutter run -d chrome

# Run in emulator (Android/iOS)
flutter run
```

---

## 📂 Project Architecture Layout

```
lib/
├── main.dart                      # App root, MultiProvider setups, and Router mapping
├── theme/
│   └── app_theme.dart             # Dark/Light layouts, Google fonts, and Glassmorphic cards
├── models/
│   ├── user_model.dart            # Roles: Admin, Organization, Donor, Volunteer
│   ├── campaign_model.dart        # Multi-modal targets: Cash, Materials, Skills
│   ├── milestone_model.dart       # Milestones tracker with status and evidence links/hashes
│   ├── pledge_model.dart          # Materials pledged, cash donated, skills volunteered
│   └── receipt_model.dart         # Digital receipt representation
├── services/
│   ├── database_service.dart      # Abstraction for database (Mock database & Firestore specs)
│   ├── pdf_service.dart           # PDF document creator using pdf package
│   ├── location_service.dart      # Haversine distance calculator and location sensor wrapper
│   └── l10n_service.dart          # Localized strings dictionary (English and Amharic)
└── views/
    ├── auth/
    │   └── login_register_view.dart # Dynamic onboarding and login screen
    ├── org/
    │   ├── org_dashboard.dart     # Milestone uploaders and dropoff confirmations
    │   └── create_campaign_view.dart # Campaign wizard form and milestones builder
    ├── donor/
    │   ├── donor_dashboard.dart   # Geolocation slider feeds and receipts log
    │   └── campaign_detail_view.dart # Details, cash inputs, and check-list pledging
    ├── volunteer/
    │   └── volunteer_matching_view.dart # Skill chips matching campaigns
    ├── admin/
    │   └── admin_panel.dart       # Verification boards for NGO documents and evidence
    └── shared/
        ├── receipt_viewer.dart    # Receipt PDF download and signature display
        └── ledger_view.dart       # Public ledger stream and chart visualization
```

---

## 🔒 Firebase/Firestore Live Toggle Integration
If transitioning from local simulation mock database into live Firebase production servers:
1. Initialize a new project in [Firebase Console](https://firebase.google.com).
2. Configure Auth (Email/Password) and Firestore Database.
3. Deploy the security rules defined in the root file: `firestore.rules` using the Firebase CLI:
   ```bash
   firebase deploy --only firestore:rules
   ```
4. Setup FlutterFire by running:
   ```bash
   flutterfire configure
   ```
5. Modify `lib/services/database_service.dart` and route queries to target live collection references rather than in-memory arrays.
