StreamX – Your Entertainment, Your Way 🎬

StreamX is an Android entertainment application designed to provide a modern, smooth, and user-friendly streaming experience.

Featuring a premium interface, intuitive navigation, and a clean visual design, StreamX brings your entertainment experience together in one place.

✨ Features

- 🎬 Modern and premium user interface
- 📱 Android-friendly experience
- 🔍 Easy content discovery and navigation
- 🌐 Online content integration
- 🎨 Smooth animations and elegant design
- ⚡ Simple and intuitive controls
- 📺 Entertainment-focused experience

📦 Download & Installation

1. Download the latest "StreamX.apk" from the Assets section below.
2. Open the downloaded APK on your Android device.
3. Allow installation from your browser or file manager if Android requests permission.
4. Complete installation and launch StreamX.

📱 Compatibility

- Platform: Android
- Distribution: APK
- Version: See release tag
- Architecture: See APK build configuration

👨‍💻 Developer

Akhil Pal

Instagram: https://www.instagram.com/iamakhil_yt/

⚖️ Disclaimer

StreamX is an independent project. It is not affiliated with or endorsed by any third-party streaming service.

Users are responsible for ensuring that their use of external content sources complies with applicable copyright laws and service terms.

❤️ Support the Project

If you like StreamX:

- Star ⭐ this repository.
- Report bugs through GitHub Issues.
- Share the project with others.

StreamX – Entertainment in a New Experience.<img width="1600" height="720" alt="Screenshot_20261031_212038" src="https://github.com/user-attachments/assets/c86548e9-1c72-4174-8ecc-9bf5fb872700" />
<img width="720" height="1600" alt="Screenshot_20261031_212022" src="https://github.com/user-attachments/assets/a580d5dc-9d97-4d39-aa51-3a5655ee8f92" />
<img width="720" height="1600" alt="Screenshot_20261031_211951" src="https://github.com/user-attachments/assets/3960f06c-118d-4683-bae5-d93370c7253c" />
<img width="720" height="1600" alt="Screenshot_20261031_211934" src="https://github.com/user-attachments/assets/1d7fbc2c-09f6-43fc-ab56-6798d2c8e448" />
<img width="720" height="1600" alt="Screenshot_20261031_211849" src="https://github.com/user-attachments/assets/46ea9637-6ed4-48a8-8996-86b7fbd38856" />
<img width="720" height="1600" alt="Screenshot_20261031_211827" src="https://github.com/user-attachments/assets/70d652d0-9941-43bf-873a-8868e2c88983" />
<img width="720" height="1600" alt="Screenshot_20261031_211808" src="https://github.com/user-attachments/assets/3dbd16a7-8fbd-4b68-9a4e-dfa4a251e1c1" />
<img width="720" height="1600" alt="Screenshot_20261031_211800" src="https://github.com/user-attachments/assets/91a057b8-6004-4745-88e8-55e5ada095d4" />
<img width="720" height="1600" alt="Screenshot_20261031_211837" src="https://github.com/user-attachments/assets/ff8ff1d6-f289-40eb-8467-426870feb4fe" />

# StreamX


StreamX branding and redesign by **Akhil Pal**. Instagram: https://www.instagram.com/iamakhil_yt/

This is the repaired supplied Ayushflix / Cloudstream-derived project, **not a new mock application**. GPL and upstream/third-party notices are retained in `LICENSE`, `UPSTREAM-README.md`, and the existing modules. Provider identifiers, package namespace, account/history/download keys and desktop storage paths are deliberately retained for compatibility.

## Delivery status

This is a **development candidate**, not a certified production release. Android unit/layout regressions and a development APK can be built here. The HTML5 player has a local decoding test using self-authored H.264/AAC media; this is not proof that a movie provider works. No Android device, licensed movie source/account, TV remote, release-signing key, or deployment is available in this environment. Consult the accompanying audit report for executed tests and blockers. No fake movie streams or production diagnostic-media fallbacks are supplied.

The official displayed product name is **StreamX**. The delivered APK filename is **StreamX.apk**. For safe side-by-side testing the validated build uses the existing isolated package `com.ayushflix.app.streamxtest.r4`; the default original package remains `com.ayushflix.app`. An isolated build does not read or migrate the original installation's data. **Keep the original installed. Never uninstall to bypass a signing mismatch.** An in-place update requires the original private signing certificate. No signing keys are distributed.

## R4 — standalone fullscreen playback host

- Video now opens in `StreamXPlayerActivity`, a dedicated Android window with one
  match-parent container, rather than the Home/details NavHost, navigation rail or dock.
- Existing Media3 resolver/headers/subtitles/resume remain; no alternative engine,
  unauthorized source or phone-model-specific branch was introduced.
- Android/Media3 own viewport measurement, aspect ratio and rotation. Dedicated-player
  pinch matrices are disabled; use native Fit/Fill/Zoom instead.
- Player view teardown releases its engine, media session, listeners, PiP receiver and
  surface binding. Incoming notifications reuse the existing session when possible.
- Diagnostics record the actual ancestor geometry and TextureView matrix on pre-draw,
  after layout, rather than reporting only calculated fit bounds.
- Startup-only artwork and existing profile/security flows are retained from R3.
- This is an isolated debug build, not an in-place update or a certified universal fix.
  Physical decoding, vendor codec differences, rotation, PiP and authorized provider
  playback still require device acceptance. No Android device is attached here.

See `docs/STREAMX-R4-REPAIR.md` and `qa/R4-DEVICE-RETEST.md`.
The R2/R3 documents remain historical, not current acceptance evidence.

## Android build

Requirements: full JDK 17, Android SDK platform `android-37.0`, build tools `36.0.0`, network access for Gradle dependencies, included Gradle wrapper. Native/plugin dependencies retain their own licensing and platform constraints.

```sh
# For an unpacked ZIP only: establish the Git metadata used by the inherited hash task.
git init
chmod +x gradlew
export JAVA_HOME=/path/to/jdk17
export ANDROID_HOME=/path/to/android-sdk
export PATH="$JAVA_HOME/bin:$PATH"
printf 'sdk.dir=%s\n' "$ANDROID_HOME" > local.properties
./gradlew :app:testStableDebugUnitTest :app:assembleStableDebug \
  -PstreamxIsolatedTest=true --no-daemon --max-workers=1 \
  -Pkotlin.compiler.execution.strategy=in-process \
  '-Dorg.gradle.jvmargs=-Xmx2000m -Dfile.encoding=UTF-8'
# On low-memory hosts, run tests and assembly in separate processes using
# qa/gradle-low-memory.init.gradle; see docs/STREAMX-R3-REPAIR.md.
cp app/build/outputs/apk/stable/debug/app-stable-debug.apk StreamX.apk
python3 tools/verify-streamx-repair.py
```

The APK is debug-signed. Release/AAB signing, Play policies, physical-device acceptance and production migration are separate release gates. Omit the isolated property only if intentionally building the original package with an appropriate signing/migration plan.

## Startup artwork

`app/src/main/res/drawable-nodpi/streamx_loading_art.png` and `tizen-wgt/assets/streamx-startup-only.png` are the same supplied **179×428 flattened portrait image**, preserved verbatim and aspect-fitted. The Android only consumer is `StreamXSplash`; the web reference is inside the removed-on-readiness startup element. The image has a baked-in frame and tagline; the implementation does not pretend these are editable vector layers. Its original resolution limits large-screen sharpness.

Subtle actual Canvas/CSS highlight/ripple overlays and an indeterminate indicator complement the flat artwork. **This is not a liquid simulation or physically animated emblem.** Reduced motion keeps the real loading screen static. Startup dismisses on local initialization readiness, failure/deadline, or lifecycle exit; no fabricated progress or forced decorative delay. Normal screens keep their normal artwork/texture, never the complete supplied splash. Original square X artwork supplies icons/brand emblems separately.

## Web/backend

```sh
npm ci --prefix server --ignore-scripts
npm test --prefix server
node server/index.js
# Open http://127.0.0.1:8080
```

Node 22+ supported; Node 24 used in validation. `server/.env.example` lists configuration names only; the program reads process environment (it does not automatically load `.env`). An unconfigured server intentionally returns actionable HTTP 503 for catalog/provider routes. Startup still dismisses; no sample movies are substituted.

The inherited provider adapter is **disabled by default**. Enable it only after independently establishing authorization, reviewing the integration and provisioning a legitimate credential with your deployment's secret manager. Setting a flag does not confer media rights. No external provider account/authentication/DRM was exercised here. Provider tokens and private URLs must not enter source, logs, browser query credentials or Git history.

The arbitrary URL/cookie DASH proxy was removed, not made public. Both old proxy routes return HTTP 410. A source requiring that relay now gets HTTP 422 with an explanation. Supporting such sources again requires a separately audited, provider-authorized relay (authentication, exact-host/IP controls, DNS pinning, redirect policy, bounded data, credential isolation). Do not restore the old proxy or bypass access controls. Direct authorized media continues through the existing HTML5/HLS.js/DASH.js adapters. The mutable remote-JavaScript auto-update and unsolicited direct-site fallback were removed for safety. Metadata never guarantees playback.

```sh
# Repository root, not server/:
docker build -f server/Dockerfile -t streamx .
```

Docker packaging is provided but not executed/verified here. No site has been deployed. A bundled Tizen client exists; signing and installing a `.wgt` requires the Tizen SDK/certificate/device and is not claimed. The separate desktop build needs JDK 21 and platform-specific native bridges; it is not a verified cross-platform installer.

## Publishing source to your GitHub repository

Unpack the source, keep all licence/notice files, review configuration, and run the checks above. Then initialize/commit/push to **your own** repository using your authenticated Git tooling. Do not publish private recordings, `.env`, local SDK paths, keys, user databases, caches or generated build directories. The delivered source excludes these. No GitHub repository has been created or pushed by this task. The included `streamx-validation.yml` is a manual/PR development check, not production signing or deployment automation.

## Acceptance still required

Use a physical phone and TV/emulator with an explicitly authorized source; record Android/device versions, first-frame latency, advancing frames, audible output, pause/resume/seek, buffering/error recovery, lifecycle/rotation and resource release. Test invalid/expired/401/403 sources separately. Repeat for each relevant codec/DRM/source class; one clip cannot prove every movie works. Cast, downloads, account flows, release shrinking, desktop natives and whole-app accessibility/performance remain device/platform release gates.

### Reproduce local browser decoding checks (optional developer tools)

From repository root, with FFmpeg, Chromium and Playwright available:

```sh
mkdir -p qa/local-media
sh tools/generate-diagnostic-media.sh qa/local-media/authorized-diagnostic.mp4
npm install --prefix server --no-save --package-lock=false --ignore-scripts playwright
CHROMIUM_PATH=/path/to/chromium node tools/verify-web-playback.cjs
```

The harness starts an ephemeral loopback server, blocks external requests, and tests the actual HTML5 media element. A catalog HTML-injection fixture is explicitly test data, never runtime media. Reports/previews go into ignored `qa/web-output/`. A decoded-audio counter is not verification of audible sound from a real device. The harness does not establish live HLS/DASH/DRM/provider compatibility.

## Optional client-service API configuration

Inherited hardcoded TMDB and OpenSubtitles client API keys have been removed from six source locations. The delivered APK was built **without** these keys. TMDB suggestions/enrichment and OpenSubtitles API functions therefore require your own authorized, appropriately restricted client configuration; no inherited key or fake result is substituted. This does not make metadata a playable movie source. Existing user-saved desktop TMDB preferences are preserved and take precedence.

Provide `STREAMX_TMDB_API_KEY` and/or `STREAMX_OPEN_SUBTITLES_API_KEY` to the Gradle build environment through your own secure configuration/CI secret store, then rebuild. Do not commit values, use server-privileged credentials in a client, or publish generated keyed build output as though client keys were secret at runtime. Build-time client keys can be extracted from APKs; a production service requiring confidential credentials needs an appropriately authorized server-side design. Previously exposed credentials need owner-side revocation/rotation. Example variable names only are in `client-keys.env.example`.

The inherited publish-on-push release workflow and scheduled upstream extension synchronization are now **manual-only**. Their bodies remain for owner review; do not run them until repository identity, signing, source authorization, update endpoints and release artifacts are verified. The new development validation workflow is separate and does not publish a production release.

An opt-in relay also requires `STREAMX_RELAY_TOKEN`; missing configuration returns 503 and missing/invalid bearer authorization returns 401 before any provider request. The local developer client can receive a token in memory through `window.STREAMX_RELAY_TOKEN`; never put that token in public static files, URLs, source or logs. A publicly deployed service still requires proper user authentication, HTTPS, rate limiting, secret management and an authorized provider agreement; the development token gate is not a complete production identity system.
