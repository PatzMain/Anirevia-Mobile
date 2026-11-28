# Patch notes

## v0.3.2 — 28 November 2026

A download stability update with automatic multi-server failover, smarter CDN retry/throttling handling, remuxer reliability fixes, and smoother progress stages.

- **Automatic multi-server download failover**: If a streaming server fails during a download, the queue now automatically switches to the next ranked server instead of failing the episode immediately.
- **Better CDN compatibility & adaptive throttling**: Uses the standard playback User-Agent, supports compressed playlists and segments, and honors HTTP `429`/`503` `Retry-After` backoff windows when CDNs rate-limit requests.
- **Stronger MP4 remuxing reliability**: Safely handles missing/unset timestamps (`C.TIME_UNSET`), ensures codec configuration (`csd-0`) is captured before muxing starts, and prevents audio-heavy opening segments from starting the muxer without the video track.
- **Clearer, monotonic download progress**: Smoothly reports **Downloading**, **Processing**, and **Verifying** stages with accurate progress scaling that never jumps to 100% early or flickers backward.
- **Android storage verification fix**: Falls back to `AssetFileDescriptor` size checks when a storage provider briefly reports `0` bytes right after saving a newly finished `.mp4`.

Update in-app through **Settings → App updates**, or install the ARM64 APK (most modern Android phones) or Universal APK (Android 7.0+ devices).

## v0.3.1 — 28 November 2026

A focused reliability update that rebuilds the download backend to save one clean `.mp4` file per episode or movie and fixes offline mode playback across the app.

- **One `.mp4` file per episode or movie**: Rebuilt the download engine to remux HLS streams (including AES-128 encrypted and separate-audio streams) and save direct MP4 sources into a single playable `.mp4` file instead of scattering multiple segment files in your download folder.
- **Clean, consistent file naming**:
  - `AnimeTitle_E01.mp4` for 2-digit episode series
  - `AnimeTitle_E001.mp4` for 3-digit episode series
  - `AnimeTitle_E0001.mp4` for 4-digit episode series
  - `MovieTitle.mp4` for movies (saved directly in your chosen download folder)
- **Faster & more reliable downloads**: Added concurrent segment prefetching with automatic per-segment retries, resilient HLS quality selection, improved server selection, smooth percentage progress in Library, and fixed a retry race condition.
- **Working Offline Mode & Offline Playback**:
  - Fixed connectivity detection when going offline so Offline Mode activates immediately.
  - Loaded your downloaded library right at startup so downloaded episodes are ready across **Home**, **Browse**, **My Lists**, **Watch**, and **Library** with zero internet.
  - Opening a series or tapping **Continue watching** / **History** while offline now shows and plays your downloaded episodes directly.
  - Offline playback now reads your single `.mp4` directly for fast seeking, serves saved captions completely offline, and restores your watch-history resume position.

Update in-app through **Settings → App updates**, or install the ARM64 APK (most modern Android phones) or Universal APK (Android 7.0+ devices).

## v0.3.0 â€” 27 November 2026

A major polish and performance milestone featuring faster startup, smart auto-landscape rotation, a fullscreen offline player, merged timeline markers, crisp haptics, and cleaner screens across the whole app.

- **Smoother app launch & instant Home**: Added a dark branded launch screen on Android 12+, instant cached Home screen loading with pull-to-refresh, and removed the startup "Loading saved listsâ€¦" banner flash.
- **Cleaner app switching**: Switching away while watching now pauses playback cleanly and keeps controls ready when you return, restores fullscreen smoothly, and opening the app icon always brings you right back to your current screen.
- **Smart portrait & auto-landscape rotation**: Home, My Lists, Browse, Library, and Settings stay locked in portrait. While watching an episode, tilting your phone sideways automatically switches to fullscreen landscape (respecting Android's Auto-Rotate setting), and tilting upright returns to portrait unless screen lock is active.
- **Fullscreen Offline Player**: Opening a downloaded episode from **Library** now launches straight into fullscreen landscape with Next/Previous downloaded episode navigation.
- **Merged intro & outro timeline markers**: Opening and ending segments now sit seamlessly inside the main progress bar and smoothly fill with orange as you watch.
- **Faster video start, instant rewind & crisp haptics**: Videos start faster and 10â€“30 second rewinds happen instantly without re-buffering, paired with subtle haptic feedback on seek taps, 2Ã— speed hold, Slide-to-Unlock, Skip Intro/Outro, bookmarks, and saving settings.
- **Standard upgraded player**: Swipe to Unlock, Skip Intro/Outro pills, and merged timeline markers are now built in by default (no longer behind an "Experimental" toggle), with a clean **Volume & brightness gestures** switch in Playback preferences.
- **Tidier Browse, Library, Settings & Player Audio menu**:
  - **Browse**: **Quick collections** and **Browse by Genre** now stay tucked inside **Filters** by default so the anime grid appears immediately.
  - **Library**: Removed the extra subheading under the Library title.
  - **Settings â†’ App updates**: Redesigned with a clear update badge, readable file sizes, and collapsible patch notes for each version.
  - **Video player**: Simplified the **Audio** menu by removing the duplicate Captions item.

Update in-app through **Settings â†’ App updates**, or install the ARM64 APK (most modern Android phones) or Universal APK (Android 7.0+ devices).

## v0.2.19 â€” 27 November 2026

Player polish, smoother rotation, simpler server selection, and important gesture fixes.

- **Fixed Slide-to-Unlock & gesture overlays**: Dragging the **SWIPE TO UNLOCK** slider now unlocks smoothly without disappearing mid-swipe, and the on-screen indicators for **2Ã— speed**, **volume**, and **brightness** gestures are back and clearly visible.
- **Fixed 2Ã— speed staying stuck**: Holding the right side of the video player for 2Ã— speed now always returns to your normal playback speed as soon as you let go.
- **Smoother portrait & fullscreen switching**: Switching between portrait and landscape while watching now transitions cleanly without restarting or resetting the video player.
- **Simpler server labels**: Replaced technical source and provider names with clean **Server 1**, **Server 2**, **Server 3**, **Server 4** options in the **Audio & server** picker and inside the video player, and removed the technical server list from **Settings**.
- **Cleaner portrait Watch screen**: Removed the extra episode status banner below the player for a tidier layout.
- **No more "saved source is no longer available" errors**: If a previously saved stream expires, Anirevia now automatically falls back to the best available working server.

Update in-app through **Settings â†’ App updates**, or install the ARM64 APK (most modern Android phones) or Universal APK (Android 7.0+ devices).

## v0.2.18 — 27 November 2026

A cleaner Watch screen, a smarter Settings page, and a major upgrade to the video player across both portrait and landscape modes.

- **Switch between SUB and DUB right inside the player**: Easily switch between Japanese (SUB) and English (DUB) audio and streaming servers while watching, with faster audio and subtitle loading.
- **New Slide-to-Unlock screen lock**: Locking the player now shows a sleek **SWIPE TO UNLOCK** slider along with the episode title and timeline (with intro and outro markers) whenever you tap the screen, then fades completely out of sight while you watch.
- **Improved Caption Style picker**: Customize subtitle size and theme with a live preview and clear highlights showing your active selections—saved automatically across episodes and fullscreen changes.
- **Refreshed Skip Intro & Skip Outro button**: Updated to a clean white pill button with a skip icon so it's easier to spot and tap.
- **Floating Save button in Settings**: Replaced the bottom "Save preferences" button with an animated floating **Save** button that only appears when you change a setting.
- **Cleaner Watch screen**: Removed unnecessary on-screen buttons (Auto-Select, Change source, and Select downloads)—best server selection now runs automatically in the background, and downloading episodes works directly from the Download button.

Update in-app through **Settings → App updates**, or install the ARM64 APK (most modern Android phones) or Universal APK (Android 7.0+ devices).
## v0.2.17 — 27 November 2026

Hotfix restoring Aniwave DUB and SUB playback on *Solo Leveling Season 2* and episodes with long provider link tokens.

- **Fixed Aniwave `sourceId` length rejection**: Compacted long Aniwave `data-link-id` hex tokens (>64 chars) into a deterministic `sha256-` digest so `NativeMediaIdentity`'s 512-character limit never silently drops Aniwave DUB/SUB streams on episodes like *Solo Leveling Season 2 -Arise from the Shadow-*.
- **Added regression test**: Verified 600-character Aniwave link IDs stay safely under the identity limit (`346` JVM unit tests passing).

Both APKs preserve the `com.anirevia.mobile` application ID (build `2017`) and production signing key so existing `0.2.16` installations update in place. Choose ARM64 for 64-bit ARM phones; the universal APK also supports x86_64 devices. Android 7.0/API 24 or later is required.

## v0.2.16 — 27 November 2026

Improved DUB/SUB streaming reliability, smarter Auto-Select server fallback, and expanded anime search matching.

- **Auto-Select Server Mode (Default ON)**: Prioritizes the best healthy server matching your preferred audio (DUB or SUB) and automatically falls back to the best SUB server when DUB is unavailable for an episode, without forcing manual server selection. Includes an **Auto-Select: ON/OFF** toggle and inline fallback notice on the Watch screen.
- **Fixed DUB provider race condition**: SUB-only providers no longer cut off DUB resolution during fast-quorum fetching when DUB is preferred, and the grace window was increased to `6s` so DUB servers (such as Aniwave for *Solo Leveling* and *Overgeared*) resolve reliably.
- **Expanded search matching**: Added possessive-apostrophe fallback queries in Browse and Search so queries like `Knights & Magic` find *Knight's & Magic* and similar punctuated titles.

Both APKs preserve the `com.anirevia.mobile` application ID (build `2016`) and production signing key so existing installations update in place. Choose ARM64 for 64-bit ARM phones; the universal APK also supports x86_64 devices. Android 7.0/API 24 or later is required.

## v0.2.15 — 23 November 2026

Reliability, stability, and speed release fixing the Settings page crash, AniList GraphQL HTTP 400 and timeout failures, and slow multi-server loading across the native Android app.

- Fixed the Settings page crash in production builds (`com.anirevia.mobile`) by removing a nested infinite `verticalScroll` layout and replacing reflection-based `OfficialUpdatesController` creation with an explicit R8-safe factory.
- Hardened Settings and in-app updater stability (avoiding stuck `Checking…` states, offloading `SharedPreferences` and storage scans to `Dispatchers.IO`).
- Fixed AniList GraphQL HTTP 400 errors and tightened `OkHttpTransport` timeouts, `Retry-After` handling, and stale-cache fallback on Home bootstrap.
- Added bounded fast-quorum multi-server resolution, AllAnime GraphQL POST memory after HTTP 403, and immediate circuit-breaker trips on DNS/TLS/schema failures.

## v0.2.14 — 22 November 2026

Native Android playback and browsing, wider SUB/DUB coverage, LiveChart release countdowns, seamless episode transitions, and experimental player gestures.

- Rebuilt on a native Kotlin and Jetpack Compose runtime (`com.anirevia.mobile`, build 2014), removing the Android System WebView requirement while preserving the five destinations (Home, My Lists, Browse, Library, and Settings), saved lists, offline downloads, and in-app updates.
- Watchable-only catalog filtering removes unreleased (`NOT_YET_RELEASED`) and zero-episode entries across Home, Search, Browse, and recommendations so only playable SUB or DUB anime are listed.
- Browse filter coverage now spans all 18 standard AniList genres plus tag-routed `Historical` and `Isekai` filters, watchable release statuses (`RELEASING`, `FINISHED`), `TV_SHORT` alongside standard formats, and expanded release years so every filter returns matching anime.
- 18+ / Hentai titles are hidden across catalog, search, and recommendations unless **Show 18+ / Adult content (Hentai)** is enabled in Settings. Entries that list episodes without playable or downloadable streams are automatically filtered out and recorded in the unplayable store.
- Expanded SUB and DUB resolution across seven providers (`AnimeParadise`, `AllAnime`, `Aniwave`, `HiAnime`, `Consumet` Zoro/Gogoanime `-dub`, `AnimeKai`, and `AnimePahe`) with custom mirror URL overrides in Settings and season/year-aware title matching for English dubs such as *Solo Leveling*.
- Cold-start and cache-clear resilience: added an 8 MiB atomic LRU disk cache (`NativeDiskCache`) for catalog shelves, series details, episode lists, and schedules, parallel Home shelf loading, Coil image memory/disk caching, per-host provider semaphores, and 60-second provider circuit breakers to prevent timeouts after clearing app data or cache.
- Airing anime pages show a live **Next Episode** countdown timer and local air date/time fetched from [LiveChart.me](https://www.livechart.me/schedule) with AniList schedule fallback.
- Seamless **Next Episode** transitions: the player pre-resolves the next episode's stream and skip intervals in the background once playback passes 75% (or within 90 seconds of the end) and switches media items in place while preserving fullscreen and audio preference.
- **Seasons & Sequels** replaces generic *More to Explore* recommendations whenever a series or movie has chronological franchise relations (`PREQUEL`, `SEQUEL`, `PARENT`, `SIDE_STORY`, `SPIN_OFF`, `ALTERNATIVE`, `SUMMARY`), linking seasons such as *Solo Leveling Season 1* and *Solo Leveling Season 2* directly.
- Cumulative double-tap seeking (`+10s`, `+20s`, `+30s` and `-10s`, `-20s`, `-30s`) now triggers crisp haptic feedback on every tap, and a single **Experimental video player features** toggle in Settings enables:
  - VLC-style **Slide to unlock** track in fullscreen when the player controls are locked.
  - Right-side vertical slide gesture for **Volume** adjustment with an on-screen percentage HUD.
  - Left-side vertical slide gesture for **Brightness** adjustment with an on-screen percentage HUD.
  - **Skip Intro** and **Skip Outro** buttons paired with a **blue timeline highlight** across opening and ending intervals on the seek bar.

Both APKs preserve the `com.anirevia.mobile` application ID and signing key so existing installations update in place. Choose ARM64 for the Realme 6 and other 64-bit ARM phones; the universal APK also supports x86_64 devices. Android 7.0/API 24 or later is required.

Validation passed: 337 Android JVM unit tests across 48 test classes (`npm run test:fast` and `:app:testDebugUnitTest`), zero Android Lint errors (`:app:lintDebug`), and verified v2/v3 signing, 16 KiB native page alignment, and package metadata on both release APKs.

## v0.2.13 — 22 October 2026

Browse, simpler mobile navigation, and updates inside Anirevia.

- Five direct destinations: Home, My Lists, Browse, Library, and Settings. My Lists combines your existing Watchlist and History without changing saved data.
- Browse brings discovery and search into one page, with compact custom filter dropdowns, genre shortcuts, removable filters, and Load more. Returning from an anime restores your filters and scroll position.
- Library keeps downloaded series, offline playback, storage information, and queue access together. Settings groups updates, playback, downloads, and sources.
- App-styled dropdowns replace Android's built-in selectors for Browse filters, Library audio, settings choices, and episode ranges. Back closes the topmost dropdown first.
- Download app updates inside Anirevia with progress, cancel, and retry. Choose Install update when ready; Android still asks for installation confirmation. If needed, Allow installation opens Android's per-app setting and returns you to the downloaded update.
- The update screen puts one recommended package first, with a full-width action, concise release notes, and expandable history. Downloaded packages are checked against the app's package ID, selected version, installed build, and signing certificates before the installer opens.
- Interrupted update downloads can be retried. Completed downloads survive app restarts, including Android restarting the app after installation permission changes. A successfully installed update clears its cached installer offer.
- Removed verified unused interface code, old artwork, and obsolete search and navigation flows. The portrait/fullscreen player, episode downloads, saved preferences, and existing recovery behavior are retained.

Both APKs preserve the application ID and signing key. Choose ARM64 for the Realme 6; universal also supports x86_64 devices. Android 7.0/API 24 or later is required.

Install 0.2.13 once using the APK or the previous updater. Its new in-app download and installation flow handles subsequent updates. Android's permission and installation confirmations remain required. Normal updates retain your settings, lists, progress, and offline episodes.

At publication (22 October 2026): seven workspace typechecks, 310 frontend tests, 106 backend tests, 72 Android JVM tests, the pinned Rust test command, and all 22 signed-APK acceptance cases on Android 16 plus its fresh-process installer-permission probe. Android 11 passed 21 of 22 cases; the real GitHub APK transfer exceeded the test’s 60-second deadline, so its additional granted-permission probe was not completed. Android 11 updater validation remains incomplete. The updater tests cover a real GitHub transfer, cancel/retry, rejected packages, cache recovery, permission return, and an intercepted installer handoff.

**Follow-up validation — 23 October 2026:** Android 11 now passes all 22 signed-APK acceptance cases and the separate granted-permission updater probe. The transfer test has a bounded 180-second network deadline, byte-progress diagnostics, and an explicit complete-APK byte check. The original timeout did not recur. This was a test-only correction; the published 0.2.13 APKs and their checksums are unchanged. Physical Realme 6 and live-provider limits still apply.

Validation covers Android 11 and Android 16 emulators, controlled fixtures, and public sample media. Physical Realme 6 hardware and live anime-provider playback are not part of this validation.


[Download v0.2.13](https://github.com/PatzMain/Anirevia-Mobile/releases/tag/v0.2.13)

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
