# Anirevia

A personal anime streaming and offline viewing app for Android.

**[Download the Android APK](https://github.com/PatzMain/Anirevia-Mobile/releases/latest)** · **[Patch notes](CHANGELOG.md)**

## Features

- Five destinations: Home, My Lists, Browse, Library, and Settings.
- Discover anime and search in Browse, with custom filters and Load more.
- Keep Watchlist, History, and saved progress together in My Lists.
- Open anime in portrait with video, episodes, downloads, and More to Explore; expand with the fullscreen button.
- Choose episode audio, captions, quality, and sources in app-styled panels, with 10-second buttons and double-tap seeking.
- Select multiple episodes, manage the download queue, choose an export folder, and play saved episodes offline.
- Download app updates inside Anirevia, follow progress, retry if needed, then confirm installation with Android.

## Install

Choose **Anirevia-Mobile-0.2.13-arm64-v8a.apk** for a compatible ARM64 phone such as the Realme 6. The **Anirevia-Mobile-0.2.13-universal.apk** also supports x86_64 devices. Open the APK on your device and follow Android's prompts. Requires Android 7.0 or later and an updated Android System WebView.

Install 0.2.13 once using the APK or the older updater. Future updates download inside the app through **Settings → App updates**. Android may ask you to allow Anirevia to install updates and always requires installation confirmation. The app checks its package identity and signing certificates before opening the installer. Normal updates preserve your settings, lists, progress, and offline episodes.

## Current status

Version 0.2.13 adds the five-tab mobile navigation, combined My Lists, Browse discovery and search, reusable custom dropdowns, a reorganized Library and Settings, and a simpler in-app updater. The 0.2.12 player controls and episode download improvements remain in place.

At publication (22 October 2026): 310 frontend tests, 106 backend tests, 72 Android JVM checks, seven workspace typechecks, Rust command checks, and all 22 signed-APK acceptance cases plus the installer-permission probe on Android 16. Android 11 passed 21 of 22 cases; its real GitHub APK transfer exceeded the test’s 60-second deadline. The additional Android 11 granted-permission probe remains incomplete. Android 11 updater validation remains incomplete. Physical Realme 6 hardware and live anime-provider playback remain unverified.

**Follow-up validation — 23 October 2026:** Android 11 now passes all 22 signed-APK acceptance cases and the separate granted-permission updater probe. The transfer test has a bounded 180-second network deadline, byte-progress diagnostics, and an explicit complete-APK byte check. The original timeout did not recur. This was a test-only correction; the published 0.2.13 APKs and their checksums are unchanged. Physical Realme 6 and live-provider limits still apply.

Android can limit background work; reopening and retrying a download may be necessary. Shared exported files remain separate from the app-managed offline library. Updates never uninstall the app or clear user data.

## About this repository

This repository contains release downloads, introductory documentation, and patch notes. Application source code, build files, credentials, and signing keys remain local.
