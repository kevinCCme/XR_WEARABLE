# Wearables + SDK Classification

A comparison of XR and smart wearables (glasses, bands, rings) with a focus on
**developer access**: does it have an SDK, what the SDK exposes, capabilities,
price, ease of use, and how hard it is to build on.

- **Ease of use** = how simple it is for an everyday user to wear and operate.
- **Dev difficulty** = how hard it is to build apps for it.
- Ratings: 🟢 Easy · 🟡 Medium · 🔴 Hard · ⚪ N/A (no SDK yet).
- **Two SDK kinds:** *on-device app SDK* (you run code on the device) vs *cloud data API* (you only read health data from a server). The table says which.
- Prices are approximate USD and include crowdfunding / early-bird where retail is not set.
- Last updated: 2026-09-17.

---

## Glasses (AR / Smart Glasses)

| Device | Type | FOV | Color | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|---|---|
| **Even Realities G2** | AR display glasses | 27.5° | Mono (green) | ✅ Even Hub SDK — [hub.evenrealities.com](https://hub.evenrealities.com/) · pkg `@evenrealities/even_hub_sdk` | Apps run in a **WebView** (code hosted server-side, display + input relayed to glasses over BLE). Exposes: display/UI + container model, input events, page lifecycle, storage/persistence, MIC + IMU sensor events, device status, packaging. Standard browser APIs (`fetch`, Canvas). Via the community `appsbridge` (off-SDK): phone magnetometer, step count, GPS over local WebSocket. No camera/speaker (device has neither). | MicroLED + waveguide HUD (640×350, 1200 nits). AI (Conversate, Translate, Transcribe, Teleprompt), notifications. Pairs with R1 ring. | $599 (prescription lens +$159) | 🟢 | 🟡 (web/JS, high-level) |
| **XREAL Aura** (Project Aura w/ Google) | Standalone spatial computing glasses | 70° | Full | ✅ Android XR (Jetpack XR / OpenXR); [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) | Full spatial stack: 6DoF tracking, hand tracking, world/tracking cameras, plane/anchor, see-through rendering, Gemini AI. Standard Android XR + Unity/Unreal/WebXR paths. | Largest XREAL FOV. Sony micro-OLED (1920×1200/eye, 120Hz), Snapdragon + X1S coprocessor, Bose audio, 4-mic. Runs Android XR standalone (no host needed). | ~$1,500 (reserve $99/$199; ships Fall 2026) | 🟡 | 🔴 (Unity / Android XR, spatial) |
| **ROG XREAL R1** (ASUS ROG) | Tethered AR gaming display glasses | ~57°\* | Full | ⚠️ [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) — mainly plug-and-play USB-C DisplayPort screen; 6DoF/AR apps need the XREAL Eye camera add-on (Beam Pro *not* required) | XREAL SDK (Unity): head/6DoF tracking, 3DoF↔6DoF mode switching (`MODE_6DOF`), RGB camera capture (via Eye, `CAMERA` permission), spatial anchors, rendering. Native 3DoF (Anchor/Follow/Ultrawide) runs on the X1 chip with no code over USB-C DP. | World's first **240 Hz** AR glasses (gaming). Micro-OLED, X1 chip, prism optics, ships with ROG Dock. *(official FOV not yet published; prism/One Pro class.)* | $849 (ships Sep 2026) | 🟢 | 🟡 (Unity/NRSDK) |
| **XREAL One Pro** | Tethered AR display glasses | 57° | Full | ⚠️ [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) — mainly plug-and-play USB-C DisplayPort screen; 6DoF/AR apps need the XREAL Eye camera add-on (Beam Pro *not* required) | XREAL SDK (Unity): head/6DoF tracking, 3DoF↔6DoF mode switching (`MODE_6DOF`), RGB camera capture (via Eye, `CAMERA` permission), spatial anchors, rendering. Native 3DoF (Anchor/Follow/Ultrawide) runs on the X1 chip with no code over USB-C DP. | Largest FOV in the prism line (~171" virtual screen). Sony 0.55" micro-OLED, 1080p/eye, 120 Hz, 700 nits, ΔE<3, X1 chip, "X Prism" flat optics, 3-mode electrochromic dimming, Sound by Bose, 87 g. | $549 (reg $649) | 🟢 | 🟡 (Unity/NRSDK) |
| **XREAL One** | Tethered AR display glasses | 50° | Full | ⚠️ [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) — mainly plug-and-play USB-C DisplayPort screen; 6DoF/AR apps need the XREAL Eye camera add-on (Beam Pro *not* required) | XREAL SDK (Unity): head/6DoF tracking, 3DoF↔6DoF mode switching (via Eye), RGB camera capture, spatial anchors, rendering. Native 3DoF runs on the X1 chip with no code over USB-C DP. | Sony 0.68" micro-OLED, 1080p/eye, 120 Hz, 600 nits, ΔE<3, X1 chip, birdbath optics, electrochromic dimming, Sound by Bose, 82 g. | $399 (reg $499) | 🟢 | 🟡 (Unity/NRSDK) |
| **XREAL 1S** | Tethered AR display glasses | ~50°\* | Full | ⚠️ [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) — mainly plug-and-play USB-C DisplayPort screen; 6DoF/AR apps need the XREAL Eye camera add-on (Beam Pro *not* required) | XREAL SDK (Unity): head/6DoF tracking, 3DoF↔6DoF mode switching (via Eye), RGB camera capture, spatial anchors, rendering. Native 3DoF runs on the X1 chip with no code over USB-C DP. | 108% sRGB. Sony micro-OLED, 1200p/eye, 120 Hz, 700 nits, ΔE<3, X1 chip, birdbath optics, auto electrochromic dimming, Sound by Bose, 82 g. Up to 500" screen. *(FOV inferred: shares One's birdbath frame/lenses.)* | $399 | 🟢 | 🟡 (Unity/NRSDK) |
| **XREAL Air 2 Pro** | Tethered AR display glasses | 46° | Full | ⚠️ [XREAL SDK](https://docs.xreal.com/) (Unity; formerly NRSDK) — plug-and-play USB-C DisplayPort screen; 3DoF/AR only via a Beam / phone host (no on-glasses chip) | XREAL SDK (Unity) via a Beam/phone host: head-tracking, rendering. No X1 chip, so no native on-glasses spatial modes. | Sony 0.55" micro-OLED, 1080p/eye, 120 Hz, 500 nits, ΔE<3, "Optic Engine 2.0" birdbath, 3-mode electrochromic dimming, 75 g. Best-selling XREAL. | $249 (reg $399) | 🟢 | 🟡 (Unity/NRSDK) |
| **Brilliant Labs Halo** (and Frame) | Open-source AI glasses | Small HUD\* | Full | ✅ [brilliant_sdk](https://github.com/brilliantlabsAR/brilliant_sdk) · [docs](https://docs.brilliant.xyz) | Host: **Python, Flutter (iOS/Android), WebBluetooth (TS)**. Device-side: **Lua 5.4** VM. Access to display (sprites/text/bitmaps), camera photo capture, IMU (accel/mag), audio streaming (Halo), tap/click events, BLE transport. Halo emulator included. | 0.2" full-color micro-OLED HUD (FOV not published), bone-conduction audio, camera, mic, Noa AI "agentic memory", ~14h battery, ~40g. Fully open source (design + code). | ~$299 (Halo); Frame ~$199 | 🟢 | 🟡 (open, well-documented) |
| **Mentra Live** (on MentraOS) | Camera smart glasses | n/a (no display) | n/a | ✅ [MentraOS](https://github.com/Mentra-Community/MentraOS) (Apache-2.0) · [docs.mentraglass.com](https://docs.mentraglass.com) · Mentra Bluetooth SDK | **TypeScript** apps run in the MentraOS phone app (cloud-connected; local miniapps since v3.0); abstracts hardware across brands. One typed `session` with managers for display, camera, mic, speaker, transcription, translation, location, notifications, storage, permissions. Multiple apps at once. Enterprise API hooks (ERP/CRM). | **No in-lens display** (camera glasses) — 1080p camera (119° *camera* FOV), 3 mics, stereo speakers, WiFi+BT, 12h+ mixed use, 43g. OS also supports display glasses (Even G2/G1, Vuzix Z100). | $449 | 🟢 | 🟢 (high-level TS, cross-device) |
| **Rokid Glasses / AR Studio** | AR / spatial glasses | 23° (Glasses) | Mono green (Glasses); Full (AR Studio) | ✅ [UXR 3.0 SDK](https://open.rokid.com/sdk?lang=en) (Unity); [Glass3 Enterprise Client SDK](https://x-docs.rokid.com/docs/en/) (Android) | UXR 3.0: **Unity 2022 LTS** on YodaOS-Master — hand gestures, voice, projections, spatial computing, display, camera. Enterprise SDK (Android): device connect/messaging, media/display, voice AI skills, camera/vision, system settings. | Consumer Rokid Glasses = dual monochrome green MicroLED + waveguide (480×398/eye, 1500 nits). AR Studio/AR Lite for full-color spatial; enterprise Glass3 for field ops. | ~$499 (Glasses); AR Studio dev kit higher | 🟡 | 🔴 (Unity spatial / Android) |
| **Meta Ray-Ban Display** (+ Neural Band) | AI display glasses + EMG wristband | 20° (mono-ocular) | Full | ✅ [Meta Wearables Device Access Toolkit](https://developers.meta.com/wearables/) (Swift/Kotlin) + Web Apps (HTML/CSS/JS) | Extend iOS/Android apps to the in-lens display, or build standalone Web Apps. Exposes in-lens display, camera, mic. **Neural Band + temple touch surface arrive as processed input events** (arrow-keys / Enter / pinch-to-select) — **no raw EMG**, and Web Apps have no raw-gesture API. Developer preview; share with up to 100 testers. | Full-color in-lens display (right eye only), camera, open-ear audio, Meta AI; Neural Band for gesture control. | $799 (includes Neural Band) | 🟢 | 🟡 (preview; Swift/Kotlin/web) |
| **Snap Spectacles 5 / Snap Specs** | Standalone AR glasses | 46° | Full | ✅ [Lens Studio + Snap OS](https://developers.snap.com/spectacles/get-started/introduction) — SIK, UI Kit, SyncKit | Build "Lenses" in Lens Studio (JS/TS). SIK = hand gestures (pinch/poke), UI Kit, SyncKit multiplayer, cloud + monetization. Full see-through AR + hand tracking. | Binocular see-through AR, hand tracking, spatial audio, fully standalone. Dev kit = Spectacles 5; consumer = Snap Specs. | Dev: $99/mo (1-yr); Specs ~$2,195 (Fall 2026) | 🟡 | 🔴 (AR / Lens Studio) |
| **Vuzix Z100 / M400** | Monocular HUD / enterprise glasses | 30° (Z100) | Mono (green) | ✅ [Vuzix SDK](https://support.vuzix.com/docs/developer-resources) (Android + iOS; camera APIs) | Full Android & iOS SDKs, Vuzix Connect demo apps, sample code. Z100 = notification/HUD display; M400 = Android wearable computer with camera/vision APIs. | Z100: 38g monochrome MicroLED waveguide HUD (640×480, right eye). M400: camera, ruggedized Android, enterprise. | Z100 $499 (dev ed. $799); M400 ~$1,800 | 🟢 (Z100) | 🟡 (Android-based) |

> **Reading the FOV / Color columns.** For tethered "display" glasses (all XREAL, Even G2, Vuzix Z100), FOV is the **diagonal angular size of a floating virtual screen** (a big TV in front of you) — *not* a full world overlay; higher ° = bigger apparent screen. For see-through spatial glasses (Aura, Snap Specs, Rokid AR Studio, Meta Ray-Ban Display) FOV is the **AR overlay area** on the real world. **Color:** *Full* = full-color RGB micro/‑OLED; *Mono (green)* = single-colour MicroLED. `*` = not officially published (inferred from the same optics family).

---

## Watches / Smartwatches

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Apple Watch** (Series / Ultra) | Smartwatch | ✅ [watchOS SDK](https://developer.apple.com/watchos/) (Xcode) | Native on-device apps in Swift/SwiftUI. HealthKit (health/workout data), WorkoutKit, Core Motion, WatchConnectivity, complications, notifications. | HR, ECG, SpO₂, temp, GPS, fall/crash detect, cellular, rich apps. | ~$399+ (Series); Ultra ~$799 | 🟢 | 🟡 (Swift; needs Mac + Apple dev) |
| **Samsung Galaxy Watch** (+ Ultra) | Smartwatch (Wear OS) | ✅ [Wear OS SDK](https://developer.android.com/training/wearables) + [Samsung Health Sensor/Data SDK](https://developer.samsung.com/health/) | Wear OS apps (Kotlin/Compose). Samsung Health **Sensor SDK** = raw BioActive sensor data (Watch4+); **Data SDK** = integrated health data across watch/ring/phone. | HR, ECG, BIA body comp, sleep apnea, GPS, apps. | ~$300+; Ultra ~$650 | 🟢 | 🟡 (Wear OS / Kotlin) |
| **Garmin** (Forerunner / Fenix / etc.) | Sport / outdoor watch | ✅ [Connect IQ SDK](https://developer.garmin.com/connect-iq/) (Monkey C) | On-device apps in **Monkey C**: Watch Faces, Data Fields, Widgets, Device Apps, Audio providers. Sensor + ANT+ access; no garbage collector (predictable perf). | GPS, HR, multisport, maps, very long battery, big sensor set. | ~$200–1,000 | 🟢 | 🟡 (Monkey C, custom language) |

---

## Rings

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Even Realities R1** | Smart ring | ⚠️ No public ring SDK — controls G2 via Even ecosystem ([Even Hub](https://hub.evenrealities.com/)) | Not exposed directly. Acts as input (tap/press/scroll) for G2 glasses; health data via Even app. | Heart rate, HRV, SpO₂, temp, respiratory, sleep, steps; controls G2; IP68; ~4-day battery. | Not public yet (G2 companion) | 🟢 | ⚪ |
| **Aivela Ring Pro** | Smart ring | ❌ None announced | — | Multi-wavelength PPG, temp, 6-axis IMU, OFN touch surface. Sleep/HRV/stress/recovery, taps/swipes, AI insights, 7-day battery, IP68, titanium, subscription-free. | ~$149–179 early / $299 retail | 🟢 | ⚪ |
| **KiWear Ring** | Gesture-control ring | ⚠️ Planned/"exploring" — not yet available ([kiwear.com](https://www.kiwear.com/)) | Announced but no public API/SDK yet. | Air-mouse (cursor/click/drag/scroll), cross-device gesture control, health tracking, gesture gaming, waterproof. | ~$199 (KS) / $249 early bird | 🟢 | ⚪ (planned) |
| **Oura Ring 4** | Health smart ring | ✅ [Oura API v2](https://cloud.ouraring.com/v2/docs) (cloud REST, OAuth) | **Cloud** REST API (not on-device). Exposes sleep, readiness, HR, HRV, SpO₂, temp, activity, workouts. Free; apps over 10 users need approval. | Sleep/readiness/activity, temp trends, HR/HRV, ~7-day battery, titanium. | $349–499 + $5.99/mo membership | 🟢 | 🟢 (simple REST/OAuth) |
| **Samsung Galaxy Ring** | Health smart ring | ⚠️ Data-only via [Samsung Health Data SDK](https://developer.samsung.com/health/data/overview.html) | No on-device apps. Data SDK surfaces ring health data (sleep, HR, activity) into your app alongside watch/phone. | Sleep, HR, activity, ~7-day battery, IP68. Deep Samsung ecosystem. | ~$400 | 🟢 | 🟡 (Samsung Health only) |
| **Ultrahuman Ring Air** | Health smart ring | ✅ [UltraSignal / Partnership API](https://www.ultrahuman.com/ultrasignal/) (cloud REST, OAuth 2.0) | **Cloud** REST API by application (OAuth 2.0, rotating refresh tokens; scopes: `profile` / `ring_data` / `cgm_data`). Exposes sleep, HRV, resting HR, skin temp, SpO₂, recovery/sleep/movement scores, plus optional CGM glucose. Dev-kit loaner program. No subscription. | Sleep, HR/HRV, temp, movement; no subscription; light titanium. | $349 (no subscription) | 🟢 | 🟡 (must apply for API access) |

---

## Bands / Wristbands

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Mudra Link** | Neural (EMG) wristband | ✅ [Mudra SDK](https://wearable-devices.github.io/) + [Mudra Studio](https://mudra-studio.com/) | App pairs the Link over BLE and exposes a **local WebSocket stream** (`ws://127.0.0.1:8766`) with **full raw surface-EMG signal** plus processed gestures (customizable), fingertip pressure, cursor/motion, dual input (D-pad + pointer); simulator included. Hardware v2 adds synchronized EMG + PPG + IMU. For XR/glasses, gaming, navigation, accessibility. | EMG neural sensing, no camera needed, controls AR/VR + smart TV + desktop, lightweight. | $249 ($299 MSRP) | 🟡 | 🟡 (API-gated, neural input) |
| **Whoop 5.0** | Fitness strap (no screen) | ✅ [WHOOP API](https://developer.whoop.com/) (cloud REST, OAuth) | **Cloud** REST API (free to call). Exposes cycles, recovery, strain, sleep, workouts, HR. Developer and each end user need a membership. | Continuous HR, HRV, strain, recovery, sleep; screenless strap. | Membership from $199/yr (hardware included) | 🟢 | 🟢 (simple REST/OAuth) |
| **Fitbit** (Charge / Sense) | Fitness band / watch | ✅ [Fitbit Web API](https://dev.fitbit.com/) (cloud REST, OAuth; Google) | **Cloud** Web API only (on-device SDK retired). Exposes steps, HR, sleep, activity, SpO₂ (intraday needs approval). | HR, sleep, SpO₂, some GPS, steps. Google account. | ~$100–160 | 🟢 | 🟢 (REST; no on-device apps) |
| **Meta Neural Band** | EMG neural wristband | ✅ via [Meta Wearables Device Access Toolkit](https://developers.meta.com/wearables/) | EMG gesture input exposed to apps for Ray-Ban Display (pinch, swipe, subtle finger moves). Ships paired with the glasses. | Surface-EMG gesture control, no camera; drives the display glasses. | Bundled in $799 Ray-Ban Display | 🟢 | 🟡 (via Meta toolkit) |

---

## Reference resources (not devices)

| Resource | What it is | Link |
|---|---|---|
| **seckincengiz/XR** | Curated "awesome" list of XR fundamentals, devices, SDKs, dev tools, ecosystem. Good starting map. | [github.com/seckincengiz/XR](https://github.com/seckincengiz/XR) |
| **awesome-even-realities-g2** | Community resources for building on Even G2. | [github.com/pangoleen/awesome-even-realities-g2](https://github.com/pangoleen/awesome-even-realities-g2) |

---

## Quick takeaways

- **Easiest to build on (glasses apps):** MentraOS (TypeScript, cross-brand, open source) and Even G2 (WebView/JS). Brilliant Labs Halo is best for fully open hardware + firmware.
- **Easiest overall:** health wearables with cloud APIs — Oura, Whoop, Fitbit, Ultrahuman. Just REST + OAuth, read data, no hardware code.
- **Watches** have the most mature on-device SDKs: Apple Watch (watchOS), Samsung/Wear OS, Garmin (Connect IQ).
- **Most powerful / hardest:** XREAL Aura, Snap Spectacles, Rokid AR Studio — full spatial computing (Unity / Lens Studio / Android XR).
- **Gesture / input SDKs:** Mudra Link and Meta Neural Band (EMG), plus hand-tracking on Snap and Rokid.
- **Rings are mostly closed for apps:** you get cloud health data (Oura, Ultrahuman) or nothing. No real on-device ring app platform yet.
- **No SDK yet:** Aivela Ring Pro, Even R1 (standalone), KiWear (planned).

---

## Sources

- Even Realities G2 — https://www.evenrealities.com/products/g2-a · Even Hub — https://hub.evenrealities.com/
- Even Realities R1 (ring) — https://www.evenrealities.com/smart-ring
- KiWear Ring — https://www.kickstarter.com/projects/kiwear/kiwear-ring-control-every-device-with-a-gesture · https://www.kiwear.com/
- Aivela Ring Pro — https://www.aivela.com/pages/aivela-ring-pro
- XREAL glasses — Aura https://www.xreal.com/us/aura · One Pro / One / 1S / Air 2 Pro specs from XREAL US shop compare table https://us.shop.xreal.com/products/xreal-one-pro · 1S https://www.xreal.com/us/1s · ROG XREAL R1 https://us.shop.xreal.com/products/rog-xreal-r1 (verified 2026-09-17) · NRSDK https://docs.xreal.com/
- Mudra Link — https://mudra-band.com/pages/mudra-link-main · SDK https://wearable-devices.github.io/ · Studio https://mudra-studio.com/ (raw-EMG stream verified 2026-09-17)
- Meta Wearables Device Access Toolkit (display access, gesture-as-input) — https://wearables.developer.meta.com/docs/develop/dat/display-overview/
- MentraOS SDK (typed session managers) — https://cloud-docs.mentra.glass/sdk/getting-started
- XREAL SDK (formerly NRSDK; 6DoF via XREAL Eye) — https://docs.xreal.com/ · migration https://docs.xreal.com/MigratingFromNRSDKToXREALSDK/intro
- Even Hub SDK feature notes — https://hub.evenrealities.com/docs/get-started/quickstart/first-app
- Brilliant Halo SDK — https://github.com/brilliantlabsAR/brilliant_sdk · https://docs.brilliant.xyz/halo/halo-sdk-python/
- Brilliant Labs SDK — https://github.com/brilliantlabsAR/brilliant_sdk · Devs — https://brilliant.xyz/pages/developers
- Rokid Open Platform — https://open.rokid.com/ · Docs — https://x-docs.rokid.com/docs/en/
- Mentra Live — https://mentraglass.com/live · MentraOS — https://github.com/Mentra-Community/MentraOS
- Meta Ray-Ban Display / Wearables Device Access Toolkit — https://developers.meta.com/wearables/
- Snap Spectacles — https://developers.snap.com/spectacles/get-started/introduction
- Vuzix Z100 / M400 — https://support.vuzix.com/docs/developer-resources
- Apple watchOS — https://developer.apple.com/watchos/
- Samsung Health / Wear OS — https://developer.samsung.com/health/
- Garmin Connect IQ — https://developer.garmin.com/connect-iq/
- Oura API — https://cloud.ouraring.com/v2/docs
- Samsung Galaxy Ring / Health Data SDK — https://developer.samsung.com/health/data/overview.html
- Ultrahuman UltraSignal — https://www.ultrahuman.com/ultrasignal/
- WHOOP developer — https://developer.whoop.com/
- Fitbit Web API — https://dev.fitbit.com/
- XR resource list — https://github.com/seckincengiz/XR
