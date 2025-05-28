# 🚀 Flutter Build Automation with Fastlane & GitHub Actions

This repository contains the setup and configuration for automating Flutter build and release workflows using **Fastlane** and **GitHub Actions**.  
Part 1 focuses on the **basic automation flow**, including:

- Setting up Fastlane in a Flutter project
- Incrementing build numbers
- Generating APKs
- Uploading to Firebase App Distribution
- Running the workflow via GitHub Actions

## 📁 Branch Info

- `part_1`: Contains the minimal working setup for build automation with Fastlane.

---

## 🛠️ Prerequisites

Before you begin:

- Flutter project set up with **Firebase App Distribution** enabled.
- **Ruby** (version >= 2.5) installed on your local machine.

---

## ⚙️ What’s Configured

### Fastlane Lanes

- `hello`: A dummy lane to validate Fastlane setup.
- `update_build_number`: 
  - Fetches the latest release from Firebase.
  - Increments the build number.
  - Updates `pubspec.yaml` using `flutter_versioner`.
- `build_apk`: Generates a release APK using `flutter build apk`.
- `distribute`: Uploads the APK to Firebase App Distribution.

### GitHub Actions

Workflow file: `.github/workflows/publish.yaml`

Jobs include:

- Checkout code
- Setup Flutter
- Install dependencies
- Setup Ruby & Bundler
- Decode value from GitHub Secrets
- Run Fastlane lanes

---

## 🔐 GitHub Secrets Setup

| Secret Key                      | Description                                           |
|-------------------------------|-------------------------------------------------------|
| `APP_ID`                      | Firebase App ID                                       |
| `GOOGLE_SERVICE_ACCOUNT_ENCODED` | Base64-encoded JSON of Firebase service account       |
