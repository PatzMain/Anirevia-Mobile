# Anirevia

A personal anime streaming and offline viewing app for Android.

**[Download the Android APK](https://github.com/PatzMain/Anirevia-Mobile/releases/latest)** · **[Patch notes](CHANGELOG.md)**

## Features

- Five destinations: Home, My Lists, Browse, Library, and Settings on a native Kotlin and Jetpack Compose Android runtime.
- Watchable-only catalog and search in Browse, with complete genre and tag filters (`Historical`, `Isekai`), an opt-in 18+ / Adult content setting, and Load more.
- Seven-provider SUB and DUB streaming resolution (`AnimeParadise`, `AllAnime`, `Aniwave`, `HiAnime`, `Consumet`, `AnimeKai`, and `AnimePahe`) with custom mirror URLs and widened dub coverage (including *Solo Leveling*).
- Live **Next Episode** countdown timers and local release dates/times powered by [LiveChart.me](https://www.livechart.me/schedule) with AniList fallback.
- Open anime in portrait with inline video, episodes, downloads, and chronological **Seasons & Sequels** (or *More to Explore* when standalone); expand with the fullscreen button.
- Seamless background-prefetched **Next Episode** transitions, cumulative double-tap seeking (`+10s`, `+20s`, `+30s` / `-10s`, `-20s`, `-30s`) with haptics, and an **Experimental video player features** toggle in Settings for VLC-style slide-to-unlock, vertical volume/brightness swipe gestures, and **Skip Intro** / **Skip Outro** buttons with blue timeline highlights.
- Keep Watchlist, History, and saved progress together in My Lists, manage offline episode downloads in Library, and download app updates inside Anirevia.

## Install

Choose **Anirevia-Mobile-0.2.14-arm64-v8a.apk** for a compatible ARM64 phone such as the Realme 6. The **Anirevia-Mobile-0.2.14-universal.apk** also supports x86_64 devices. Open the APK on your device and follow Android's prompts. Requires Android 7.0 (API 24) or later.

If you already have 0.2.13 installed, you can update to 0.2.14 directly through **Settings → App updates** or by installing the new APK over your existing installation. Android may ask you to allow Anirevia to install updates and always requires installation confirmation. The app checks its package identity and signing certificates before opening the installer. Normal updates preserve your settings, lists, progress, and offline episodes.

## Current status

Version 0.2.14 completes the native Android runtime migration and adds watchable-only catalog filtering, complete Browse genre/tag filters, an opt-in 18+ content gate, seven-provider SUB/DUB resolution, cold-start disk caching and circuit-breaker resilience, LiveChart.me episode countdowns, seamless prefetched Next Episode playback, chronological Seasons & Sequels recommendations, cumulative double-tap seek haptics, and the single-toggle experimental player feature suite (VLC slide-to-unlock, left brightness swipe, right volume swipe, and Skip Intro / Skip Outro with blue timeline highlights).

At publication: 337 Android JVM unit tests across 48 test classes and `:app:lintDebug` passed with zero errors, and both signed release APKs (`arm64-v8a` and `universal`) verified package identity (`com.anirevia.mobile`, versionCode `2014`), v2/v3 signing certificate continuity, and 16 KiB zip/ELF page alignment.

Android can limit background work; reopening and retrying a download may be necessary. Updates never uninstall the app or clear user data.

## About this repository

This repository contains release downloads, introductory documentation, and patch notes. Application source code, build files, credentials, and signing keys remain local.
