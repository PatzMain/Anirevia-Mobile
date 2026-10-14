# Patch notes

## v0.1.0 — 14 October 2026

### Added

- Standalone Android app using Tauri Mobile, TypeScript and Rust.
- Native fullscreen playback, watch progress and episode/source selection.
- Native HTTPS requests and persistent settings, watchlist and history.
- Batch episode selection with two simultaneous downloads and foreground progress notifications.
- Pause, resume, retry and remove actions for downloads.
- Persistent offline media cache and an offline library.
- English caption caching when supported by the chosen source.
- Personally signed universal APK for ARM64 and x86_64.

### Validation

- 85 web tests, 7 Android JVM tests, 2 Rust tests and 3 Android instrumentation checks passed.
- The packaged APK downloaded a public video fixture, played it online and played its saved copy with Wi-Fi and cellular disabled.
- APK signatures and 16 KB alignment checks passed.

### Known limitations

- Physical-phone and live anime-provider playback have not yet been established on Android.
- The headless emulator's optional screenshot check returned a black image; visual appearance needs validation on a rendering-capable device.
- Downloads remain in app-managed offline storage; shared-folder MP4 export, desktop FFmpeg full decode and SHA-256 verification are not implemented.
- Smaller conversion, PC library synchronization and guaranteed force-stop/reboot recovery are not included.
- Expired sources or interrupted preparation require retry. Android can limit background service runtime.

[Download v0.1.0](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.1.0)
