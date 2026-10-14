# Study Tracker PWA

This package preserves the original Study Tracker UI and JEE/NEET task/chapter features, and adds installability, offline app-shell caching, plus JSON backup/restore.

## What's included
- `index.html` — your app, adapted for PWA installation
- `manifest.json` — app name, display mode, and icons
- `sw.js` — service worker for app-shell caching/offline opening
- `icons/` — app icons

## Run locally on your Linux laptop
Service workers and PWA install prompts require HTTPS or localhost. From this folder run:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in Chrome/Chromium. For installation, use the browser's install option if shown. Localhost is for testing on the laptop; other devices need a secure hosted URL or a properly configured local HTTPS setup.

## Install on Android / tablet
1. Deploy the contents of this folder to an HTTPS static host (for example, GitHub Pages or Vercel).
2. Open the deployed URL in Chrome on Android.
3. Use the browser menu and choose **Install app** or **Add to Home screen**.
4. Open it once while online so the service worker can cache the app shell. Then test airplane mode.

## Back up / transfer data without accounts
- Tap **Backup** in the app to download a JSON file.
- Transfer that file by USB, Nearby Share, or another file-transfer method.
- Open Study Tracker on the destination device and tap **Restore**, then select the JSON file.
- Restore replaces the destination device's current app data. Export a backup first if you need to keep both copies.

Browser storage remains separate on each device. USB does not provide automatic browser-to-browser synchronization. This backup flow is manual and does not merge simultaneous changes.

## Android APK later
The PWA can be packaged later. For a Play Store-style APK/AAB, a Trusted Web Activity (Bubblewrap) is a good route once the app is deployed on HTTPS and you own/configure the domain. A Capacitor wrapper is another option if you want a native Android project and plugins. APK packaging/signing and device testing are not included in this PWA starter.

## Important notes
- Data is currently stored locally in each browser profile; no accounts or cloud backend are added.
- The app uses Google Fonts when online; the system font stack remains available if the font cannot load.
- Check the exam syllabus list before relying on it as an authoritative current syllabus.
