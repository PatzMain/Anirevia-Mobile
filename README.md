# Anirevia-Mobile

A personal anime streaming and offline viewing app for Android, built with Tauri Mobile, TypeScript and Rust.

**[Download the Android APK](https://github.com/PatzMain/Anirevia-Mobile/releases/latest)** · **[Patch notes](CHANGELOG.md)**

## Features

- Browse anime and choose available episode sources.
- Watch through a native player with saved progress.
- Select multiple episodes and manage a background download queue.
- Play saved episodes from an offline library without a running PC.

## Install

Open the latest release. For a compatible ARM64 phone, choose the smaller `Anirevia-Mobile-0.2.4-arm64-v8a.apk`; the `Anirevia-Mobile-0.2.4-universal.apk` also supports x86_64 emulators. Open the APK on your device to install. Android may ask you to allow installation from your browser or file manager.

Requires Android 7.0 or later and an updated Android System WebView. The APK supports ARM64 phones and x86_64 emulators. Checksums and detailed installation notes accompany each release.

## Current status

Version 0.2.4 brings smaller app downloads and a recommended APK choice on the update page. The optimized release passed native playback, download and offline checks on an Android emulator using public video fixtures. Physical-phone behavior and live anime playback on Android still need validation; provider availability varies.

Saved episodes use app-managed storage. Shared-folder MP4 export and desktop-style full-file verification are not included. Uninstalling or clearing app storage removes saved episodes. Android may limit background work; reopening and retrying can be necessary.

## About this repository

This repository contains release downloads, introductory documentation and patch notes. Application source code, build files, credentials and signing keys are not published here.
