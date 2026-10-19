# Anirevia

A personal anime streaming and offline viewing app for Android, built with Tauri Mobile, TypeScript and Rust.

**[Download the Android APK](https://github.com/PatzMain/Anirevia-Mobile/releases/latest)** · **[Patch notes](CHANGELOG.md)**

## Features

- Browse anime with larger cover artwork, quick sort choices and compact filters.
- Choose episodes beside wide thumbnails; keep the synopsis under Details.
- Open episodes in a portrait player with saved progress, episode switching, Download buttons and optional fullscreen.
- Change SUB/DUB and captions inside the player.
- Select multiple episodes and manage a background download queue.
- Choose a folder for MP4 downloads, with one subfolder per anime.
- Play saved episodes from an offline library without a running PC.

## Install

Open the latest release. For a compatible ARM64 phone, choose the smaller `Anirevia-Mobile-0.2.8-arm64-v8a.apk`; the `Anirevia-Mobile-0.2.8-universal.apk` also supports x86_64 emulators. Open the APK on your device to install. Android may ask you to allow installation from your browser or file manager.

Requires Android 7.0 or later and an updated Android System WebView. The APK supports ARM64 phones and x86_64 emulators. Checksums and detailed installation notes accompany each release.

## Current status

Version 0.2.8 improves loading and anime-to-episode navigation, adds episode switching and downloading to portrait playback, and fixes reproduced Android 11 and older-WebView compatibility failures.

Choose a download folder in Settings or before starting a batch. Episodes are saved as MP4 files inside a separate folder for each anime, while an app-managed copy supports offline playback. Existing offline episodes can also be saved to your folder, and failed folder saves can be retried without downloading again. Files in the selected folder remain when the app or its offline copy is removed. External English WebVTT captions save beside the video; manifest-only captions remain available in the app and missing exported captions are labelled. Android may limit background work; reopening and retrying can be necessary.

## About this repository

This repository contains release downloads, introductory documentation and patch notes. Application source code, build files, credentials and signing keys are not published here.
