# Patch notes

## v0.2.12 — 22 October 2026

A refreshed mobile player and simpler episode downloads.

- Compact portrait controls keep playback above the episode list. Tap the video to play; use the fullscreen button to expand it, and Back to return to portrait.
- Fullscreen follows the approved design: outline controls on dark circular buttons, title and episode at the top, separate timestamps above the orange timeline, speed and caption language on the left, and settings and exit on the right.
- Double-tap the right side to seek forward 10 seconds or the left side to rewind 10 seconds, matching the buttons. Seeking preserves paused or playing state, shows circular feedback, and respects screen lock and open panels.
- Audio, captions, quality, speed and source choices use the app's charcoal and orange styling. Options open as a portrait bottom sheet or fullscreen side panel, with a compact speed grid.
- Audio availability is checked for the selected episode. SUB-only, DUB-only, both and unknown availability are handled separately; confirmed unavailable choices are disabled. Source changes retain the current session and position, and a failed replacement keeps the current stream available.
- The download selector uses compact episode, audio and quality controls. Add more episodes in place, review the selection, and skip episodes already saved or queued with the same audio choice.
- Captions stay readable above the controls. Button touch targets follow their visible positions, timestamps fade with the player controls, and fullscreen settings avoid the system navigation-bar gutter.

The recovery and request optimizations introduced in 0.2.11 remain in place. Both APKs preserve the existing signing key and application ID. Choose the ARM64 APK for the Realme 6; the universal APK also supports x86_64 devices. Android 7.0/API 24 or later is required.

Validation passed: seven workspace typechecks, 286 frontend tests, 106 backend tests, 68 Android JVM tests, Rust command checks, and all 21 signed-APK acceptance cases on both Android 11 and Android 16.

Validation uses Android 11 and Android 16 emulators, public sample video and controlled catalog fixtures. Physical Realme 6 hardware and native playback of live anime-provider streams remain unverified.

[Download v0.2.12](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.12)

## v0.2.11 — 21 October 2026

Backend request optimization and general episode recovery, preserving the 0.2.10 mobile interface.

- Repeated catalog, episode and source requests share in-flight work and short-lived caches. Leaving a page cancels unused native HTTP requests, including queued work. Catalog cancellation supports older Android 11 WebViews.
- Provider document requests run with bounded concurrency, response sizes, deadlines and retry budgets. DUB-only resolution skips SUB-only provider work; validated results survive another provider reaching its deadline.
- Every episode uses the same recovery policy. Playback retries eligible transient failures and can try up to three different compatible source URLs within a bounded recovery window, while retaining position, pause state and player preferences.
- Download preparation and failed transfers can recover from compatible alternatives in the native background service. Recovery preserves the anime, actual episode number and audio choice. Pausing or removing a job prevents delayed work from restarting it.
- Resuming a prepared download reuses its native request and partial cache without resolving its sources again. Explicit retry refreshes episode source URLs while retaining reusable catalog metadata.
- Source changes discard source-specific burned-in-caption confirmation. Storage and permission failures remain visible without automatic redownloads; unsupported streams can fall back within the same bounded budget.

A deterministic resolver fixture measured zero additional HTTP calls for a repeated warm lookup, versus six in 0.2.10, and 18 DUB-only calls versus 25. Full SUB/DUB discovery makes more cold requests than 0.2.10 because it prepares more validated fallback choices. These are request counts from injected responses, not phone timing or bandwidth measurements.

Choose the ARM64 APK for the Realme 6. Both APKs retain the existing signing key and application ID and can update earlier releases.

Validation passed: seven workspace typechecks, 271 frontend/service tests, 106 backend tests, 68 Android JVM tests, Rust command checks, and all 20 signed-APK acceptance cases on both Android 11 and Android 16. Validation uses public sample media and controlled catalog fixtures. Physical Realme 6 hardware and native playback of live anime-provider streams remain unverified. Recovery cannot supply an episode when every compatible provider fails.

[Download v0.2.11](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.11)

## v0.2.10 — 21 October 2026

Better phone spacing, episode source recovery, and a redesigned mobile download library.

- Android now reserves system-bar and cutout space once. The web layout does not add it again, and already-fitted phone windows do not receive extra top or bottom padding.
- The portrait player and Android Back handling reconnect to the current window after it is recreated, including when switching between gesture and button navigation.
- The episode resolver now checks later servers when its initial choices fail, with up to six servers for each audio language. This applies across series and episode numbers.
- A failed alternate-title search no longer discards successful AnimeParadise matches. Source status now reflects both completed provider checks.
- Downloads uses the app's charcoal, white and orange palette. Downloaded episodes start with a two-column series grid, posters and episode counts; opening a series shows compact episode rows.
- The queue keeps progress, pause, resume and retry controls visible. Saved rows retain Play, with file paths and folder controls under More; export failures and caption warnings remain visible.
- The download library and manager share styling, including on older Android 11 WebViews. Android Back returns from episode rows to the series grid.

Choose the ARM64 APK for the Realme 6. Both APKs retain the existing signing key and application ID and can update earlier releases.

Validation passed: seven workspace typechecks, 238 frontend tests, 106 backend tests, 35 Android JVM tests, Rust command checks, and all 14 signed-APK acceptance cases on both Android 11 and Android 16. Validation uses public sample media and controlled catalog fixtures. Physical Realme 6 hardware and native playback of live anime-provider streams remain unverified. Live availability and English subtitles depend on the provider; no subtitle evidence is fabricated.

[Download v0.2.10](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.10)

## v0.2.9 — 19 October 2026

One mobile flow: Home and search → a single portrait page with video, episodes, downloads and More to Explore.

- Anime cards and search results open the portrait series page. Choose an episode to start playback in the player at the top; the episode list and recommendations stay below it.
- Episode and streaming-source changes reuse the same player in the main screen. Fullscreen is optional and returns to the portrait page.
- Source menus use a stable list and close when the episode or source list changes. Late source requests cannot reopen a page you left or replace a newer selection.
- Fixed an Android 11 crash reproduced with streaming captions that have no track ID.
- Audio and server choices stay selected. Changing a matched streaming version clears the previous playback and loads its episode list without autoplay.
- Individual and batch downloads open from the episode list. The video pauses while download options or search are open and restores its previous playback state when they close.
- Home, series and episode loading use skeletons. Long episode lists are paginated and retain fractional episode numbers.
- Phone headers and bottom actions clear Android's status and navigation bars, including older Android 11 WebViews.
- Includes the Android 11 export and older-WebView compatibility fixes from 0.2.8.

Choose the ARM64 APK for the Realme 6. Both APKs retain the existing signing key and application ID and can update earlier releases.

Validation passed: seven workspace typechecks, 233 frontend tests, 104 backend tests, 35 Android JVM tests, Rust command checks, and all 14 signed-APK acceptance cases on both Android 11 and Android 16. Validation uses public sample media and controlled catalog fixtures. Physical Realme 6 hardware and live anime-provider playback remain unverified; source and caption availability depend on the provider.

[Download v0.2.9](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.9)

## v0.2.8 — 19 October 2026

Smoother browsing and a portrait player that keeps episode selection close at hand.

- Home shelves, anime details and episode loading use skeletons shaped like the content they replace. Selecting an anime shows its available artwork and title while the remaining details load.
- Anime cards and search results open the series information and episode list. Playback starts after selecting an episode.
- The portrait player now includes the series' episode list, with watch and Download buttons. Long lists are paginated, and fractional or nonsequential episode numbers are preserved.
- Download opens the selected episode's existing audio, quality, caption and folder options with playback paused. Continue episode resumes the saved position. Fullscreen remains optional.
- Fixed a reproduced Android 11 crash during MP4 preparation and compatibility problems affecting older Android System WebViews, including search parameters and loading styles.
- Folder exports on Android 11 and older use platform-compatible MP4 formats, converting unsupported tracks when necessary. A failed folder save retains the app's offline copy for retry.
- Added recovery screens for navigation and player startup failures.

Both APKs retain the existing application ID and signing key and can update earlier releases. Choose the ARM64 APK for compatible ARM64 phones, including the Realme 6; the universal APK also supports x86_64 emulators.

Validation passed: seven workspace typechecks, 228 frontend tests, 104 backend tests, 35 Android JVM tests, and all 12 signed-APK acceptance cases on both Android 11 and Android 16. Tests used public sample media. Physical Realme hardware and live anime-provider playback remain unverified; source and caption availability depend on the provider.

[Download v0.2.8](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.8)

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
