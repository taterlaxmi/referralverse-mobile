# ReferralVerse Mobile App 📱

This repository contains the **Native Android Container** for [ReferralVerse](https://referralverse.in), built using **Capacitor 6+**.

---

## 🏛️ Architecture Overview

ReferralVerse operates on a clean decoupled dual-repository architecture:
1. **Web Repository (`ReferralVerse`)**: Core Next.js React application, API endpoints, and mobile UI detection hooks (`BottomNav.tsx`).
2. **Mobile Repository (`ReferralVerse-Mobile`)**: Native Android shell wrapping the live website inside an advanced native Webview.

```
┌────────────────────────────────────────┐         ┌────────────────────────────────────────┐
│         ReferralVerse (Web Repo)       │         │    ReferralVerse-Mobile (Mobile Repo)  │
├────────────────────────────────────────┤         ├────────────────────────────────────────┤
│ • Next.js & React source code          │ ◄────── │ • Native Android Project (android/)    │
│ • BottomNav.tsx & useCapacitor.ts      │  Loads  │ • App Icons & Splash screens (assets/) │
│ • @capacitor/core & @capacitor/app     │ Web URL │ • capacitor.config.ts (server.url)     │
└────────────────────────────────────────┘         └────────────────────────────────────────┘
```

### ⚡ Key Features of this Mobile App Shell:
- **Live URL Wrapper**: Configured in `capacitor.config.ts` (`server.url: 'https://referralverse.in'`). App updates to the web UI are instantly reflected without requiring App Store updates.
- **Java 21 Toolchain**: Pre-configured in Gradle to ensure flawless compilation across all development environments.
- **Native Splash Screen & Icons**: Optimized using `@capacitor/assets`.
- **Native Hardware Bridge**: Handles Android physical back button navigation seamlessly via the web app's `useCapacitor` hook.

---

## 🛠️ Prerequisites

To run or build this Android project locally, ensure you have:
1. **Node.js** (v20+ recommended)
2. **Java JDK 21** (Required by Gradle for Android 34+)
   > [!IMPORTANT]
   > **Windows Users:** To guarantee out-of-the-box seamless compilation, `set JAVA_HOME=C:\Program Files\Java\jdk-21.0.10` is explicitly embedded inside `android\gradlew.bat`. This ensures Gradle and Capacitor automatically locate Java 21 regardless of external system environment variables.
3. **Android Studio** (with Android SDK 34/35 installed)

---

## 🚀 Getting Started & Local Development

### 1. Installation
Clone this repository and install the native Capacitor CLI and plugins:
```bash
git clone https://github.com/taterlaxmi/referralverse-mobile.git
cd referralverse-mobile
npm install
```

### 2. Synchronize Native Assets
Sync any updated Capacitor plugins or configuration changes to the Android project:
```bash
npm run sync
```

### 3. Run on Device or Emulator
Launch the app directly onto an active Android emulator or physical USB-connected device:
```bash
npm run run
```

### 4. Open in Android Studio
For advanced native debugging or signing release APKs/AABs:
```bash
npm run open
```

---

## 📦 Building for Production (APK / App Bundle)

To generate a standalone release APK or Android App Bundle (AAB) for publishing to the **Amazon Appstore** or Google Play:

### Via Command Line:
```bash
npm run build
```
Outputs will be located in `android/app/build/outputs/apk/release/` or `bundle/release/`.

### Via Android Studio:
1. Open Android Studio (`npm run open`).
2. Go to `Build` > `Generate Signed Bundle / APK...`.
3. Choose APK or App Bundle, provide your keystore credentials, and build.
