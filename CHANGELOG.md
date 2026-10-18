# Patch notes

## v0.2.7 — 18 October 2026

Anime and episode selection now follow the same streaming-focused design as the player.

- A charcoal palette, orange actions, larger artwork and compact navigation bring browsing and playback together while retaining Anirevia's branding.
- Discover keeps search visible, with quick Trending, Popular, New and Top rated choices. Genre, season and status filters expand when needed, retain their URL state and can be reset.
- Series pages show key artwork, a clear Watch/Resume action and separate Episodes and Details tabs. Episodes are visible before the full synopsis and metadata.
- Wide episode thumbnails, readable titles and actual watch progress make choosing the next episode easier. A finished episode offers the next listed episode, including nonsequential and fractional numbers.
- Offline download selection shows checkboxes only while saving episodes. Range and batch selection remain available, and selections survive tab changes. Changing series resets the selection controls together.
- Source matches that need confirmation remain visible. Confirmed matches are compact and can be changed.

Portrait playback, optional fullscreen, SUB/DUB and captions inside the player, chosen download folders and automatic per-anime folders remain available. Caption and source availability depend on the selected provider.

Both signed APKs retain the application ID and signing key used by previous releases. Install the ARM64 APK on compatible ARM64 phones, or the universal APK for ARM64 and x86_64.

The repository remains private and contains documentation and release downloads. Application source and signing credentials are not uploaded.

[Download v0.2.7](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.7)

## v0.2.6 — 18 October 2026

Episodes now open directly in a redesigned mobile player.

- The app's display name is **Anirevia**.
- Playback starts in portrait with a 16:9 video above the episode details. Use the fullscreen control for landscape viewing; Back returns to portrait before leaving the episode.
- Compact controls, an orange progress bar, and a single playback settings action make more room for the video.
- Change SUB/DUB and streaming sources inside **Audio & captions**, with playback position and pause state retained. When the preferred audio is unavailable, choose an available version in the player.
- Caption controls show readable language names, support regional language tags, and retain the source's selectable subtitle tracks. External WebVTT, SRT, SSA/ASS and TTML tracks use their appropriate media formats. Missing language metadata is described explicitly.
- External captions load into the video renderer. Unavailable or malformed caption files are identified without blocking playback; another working track can still be selected.

Caption availability still depends on the source. A source without a selectable caption track displays an explanation; subtitles already burned into the picture cannot be switched off. Download folder selection and automatic per-anime folders remain available.

Install the ARM64 APK on a compatible ARM64 phone, or use the universal APK for ARM64 and x86_64. Both retain the existing application ID and signing key so they can update previous releases.

The repository remains private and contains documentation and release downloads. Anonymous in-app update checks cannot read private GitHub releases.

[Download v0.2.6](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.6)

## v0.2.5 — 18 October 2026

Choose where your downloaded episodes go.

- Choose a download folder in Settings or before starting a batch, using Android's folder picker. The app remembers access across restarts.
- Anirevia automatically creates a folder for each anime and saves episodes there as MP4 files. Each batch keeps its selected location.
- Existing offline episodes can also be saved to your selected folder. Folder-save progress and failures appear beside the episode; retry a failed save without downloading the episode again.
- Saved MP4 files remain in your chosen folder when you remove the app's offline copy or uninstall Anirevia. The app also keeps its offline copy for in-app playback, so allow space for both.

External English WebVTT captions save beside the MP4. English captions carried inside an HLS/DASH manifest remain available in the app; SUB exports without those captions show a warning. Burned-in captions remain in the video.

Android limits selection of storage roots and the Downloads root. Create or select a subfolder such as Downloads/Anirevia. If access is revoked or a drive is disconnected, select the folder again and retry saving. Existing files are not overwritten or removed.

Install the ARM64 APK on a compatible ARM64 phone, or use the universal APK for ARM64 and x86_64. Both retain the existing application ID and signing key so they can update previous releases.

The repository remains private and contains documentation and release downloads. Anonymous in-app update checks cannot read private GitHub releases.

[Download v0.2.5](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.5)

## v0.2.4 — 17 October 2026

A smaller download for Android, with your familiar player and offline library.

### What's improved

- A smaller APK for ARM64 phones, plus a universal APK for compatible phones and emulators.
- The update page highlights the smaller phone APK when it matches your device.
- A lighter app package with unused browser-player files removed.
- Playback, subtitles and offline downloads have been checked again for this update.

Use the ARM64 APK on a compatible phone, or choose universal when unsure. Updating remains optional; your saved episodes stay in place when you update over your existing installation.

[Download v0.2.4](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.4)

## v0.2.3 — 16 October 2026

### Simpler downloads

- Just two views: Queue and Downloaded.
- Each episode shows its progress and one main action, such as Pause, Resume or Play.
- Open More for file details, Cancel and other options.
- Paused downloads and problems stay easy to find.
- The cleaner layout fits phones, tablets and desktop windows.

### Skip the opening and ending

- **Skip Opening** and **Skip Ending** appear during an anime opening or ending when matching timings are available.
- Tap once to jump past that section. Undo lets you go back if you tapped by mistake.
- Skipping the ending keeps scenes that come after its marked end.
- Automatic opening skips remain optional in Settings. Manual skipping is the default.

Some episodes do not have matching timing information, so the skip buttons may not appear for every episode.

Your existing library, downloads and settings are kept.

[Download v0.2.3](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.3)

## v0.2.2 — 16 October 2026

A fresh look and smoother everyday use.

### What's new

- A new koi logo and matching plum, coral and jade colors, shared with Anirevia Desktop.
- A more comfortable layout for small phones, larger screens, tablets and landscape viewing.
- Update choices now work consistently across Mobile and Desktop, with each app showing its own releases. You choose when to download and install.

### Improvements

- Smoother search while typing, with results that stay matched to your current search.
- Fixed older search results briefly appearing after closing and reopening search.
- Fewer unnecessary checks while the app is idle. Download progress catches up when you return to the app or start a download.

### Installing

Download the APK below and open it on your Android device. Android 7 or later is required. You can update the previous official build without uninstalling it. Updating is optional.

Saved episodes stay inside Anirevia's offline library. Actual download speed depends on the source and your connection.

**Update availability:** automatic checks cannot see releases while this repository remains private.

[Download v0.2.2](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.2)

## v0.2.1 — 15 October 2026

- Optional update notices with View update, Later and Skip version.
- An App updates page with a summary of each release and available APKs from version 0.2.1 onward.
- Automatic checks can be turned off, and manual checking remains available.
- Previously loaded release notes can be read offline.
- A warning before choosing an older version, since installing it may require uninstalling the app and removing saved data.

[Download v0.2.1](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.1)

## v0.1.0 — 14 October 2026

The first Android release introduced browsing, fullscreen watching, saved watch progress and an offline library. Episodes can be selected individually or in groups, with controls to pause, retry or remove downloads.

Subtitles depend on what the chosen source provides. Saved episodes remain inside the app, and Android may limit background downloads.

[Download v0.1.0](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.1.0)
