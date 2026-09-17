# Wearables + SDK Classification

A comparison of XR and smart wearables (glasses, watches, rings, bands, VR/MR
headsets, earbuds, EEG headbands, AI pendants, CGM sensors) with a focus on
**developer access**: does it have an SDK, what the SDK exposes, capabilities,
price, ease of use, and how hard it is to build on.

- **Ease of use** = how simple it is for an everyday user to wear and operate.
- **Dev difficulty** = how hard it is to build apps for it.
- Ratings: 🟢 Easy · 🟡 Medium · 🔴 Hard · ⚪ N/A (no SDK yet).
- **Two SDK kinds:** *on-device app SDK* (you run code on the device) vs *cloud data API* (you only read health data from a server). The table says which.
- Prices are approximate USD and include crowdfunding / early-bird where retail is not set.
- Last updated: 2026-09-16.

---

## Glasses (AR / Smart Glasses)

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Even Realities G2** | AR display glasses | ✅ Even Hub SDK — [hub.evenrealities.com](https://hub.evenrealities.com/) · pkg `@evenrealities/even_hub_sdk` | Apps run in a **WebView**. Exposes: display/UI render + container model, input events, page lifecycle, storage/persistence API, device APIs, packaging. Standard browser APIs (`fetch`, Canvas). Via `appsbridge`: phone magnetometer, step count, GPS over local WebSocket. No camera (device has none). | Monochrome HUD display, AI (Conversate, Translate, Transcribe, Teleprompt), notifications. Pairs with R1 ring. | $599 (prescription lens +$159) | 🟢 | 🟡 (web/JS, high-level) |
| **XREAL Aura** | Spatial computing glasses | ✅ Android XR (Jetpack XR / OpenXR); legacy [XREAL NRSDK](https://docs.xreal.com/) (Unity) | Full spatial stack: 6DoF tracking, hand tracking, world/tracking cameras, plane/anchor, see-through rendering, Gemini AI. Standard Android XR + Unity/Unreal/WebXR paths. | 70° FOV Sony micro-OLED (1920×1200/eye, 120Hz), Snapdragon + X1S coprocessor, Bose audio, 4-mic. Runs Android XR. | ~$1,500 (ships Fall 2026) | 🟡 | 🔴 (Unity / Android XR, spatial) |
| **Brilliant Labs Halo** (and Frame) | Open-source AI glasses | ✅ [brilliant_sdk](https://github.com/brilliantlabsAR/brilliant_sdk) · [docs](https://docs.brilliant.xyz) | Host: **Python, Flutter (iOS/Android), WebBluetooth (TS)**. Device-side: **Lua 5.4** VM. Access to display (sprites/text/bitmaps), camera photo capture, IMU (accel/mag), audio streaming (Halo), tap/click events, BLE transport. Halo emulator included. | Color micro-OLED display, bone-conduction audio, camera, mic, Noa AI "agentic memory", ~14h battery, ~40g. Fully open source (design + code). | ~$299 (Halo); Frame ~$199 | 🟢 | 🟡 (open, well-documented) |
| **Mentra Live** (on MentraOS) | Camera smart glasses | ✅ [MentraOS](https://github.com/Mentra-Community/MentraOS) (Apache-2.0) · [docs.mentraglass.com](https://docs.mentraglass.com) · Mentra Bluetooth SDK | **TypeScript** cloud apps run on phone runtime; abstracts hardware across brands. Access to camera, microphones, speakers, display, live captions, AI, photo capture, view streaming. Multiple apps at once. Enterprise API hooks (ERP/CRM). | 1080p camera (119° FOV), 3 mics, stereo speakers, WiFi+BT, 12h+ mixed use, 43g. OS also supports Even G2/G1, Vuzix Z100. | $449 | 🟢 | 🟢 (high-level TS, cross-device) |
| **Rokid Glasses / AR Studio** | AR / spatial glasses | ✅ [UXR 3.0 SDK](https://open.rokid.com/sdk?lang=en) (Unity); [Glass3 Enterprise Client SDK](https://x-docs.rokid.com/docs/en/) (Android) | UXR 3.0: **Unity 2022 LTS** on YodaOS-Master — hand gestures, voice, projections, spatial computing, display, camera. Enterprise SDK (Android): device connect/messaging, media/display, voice AI skills, camera/vision, system settings. | Consumer Rokid Glasses (AI + display); AR Studio/AR Lite for full spatial; enterprise Glass3 for field ops. | ~$699 (Glasses); AR Studio dev kit higher | 🟡 | 🔴 (Unity spatial / Android) |
| **Meta Ray-Ban Display** (+ Neural Band) | AI display glasses + EMG wristband | ✅ [Meta Wearables Device Access Toolkit](https://developers.meta.com/wearables/) (Swift/Kotlin) + Web Apps (HTML/CSS/JS) | Extend iOS/Android apps to the in-lens display, or build standalone Web Apps. Exposes in-lens display, camera, mic, and **Neural Band EMG gestures** (subtle finger/hand). Developer preview; share with up to 100 testers. | Color in-lens display, camera, open-ear audio, Meta AI; Neural Band for gesture control. | $799 (includes Neural Band) | 🟢 | 🟡 (preview; Swift/Kotlin/web) |
| **Snap Spectacles 5 / Snap Specs** | Standalone AR glasses | ✅ [Lens Studio + Snap OS](https://developers.snap.com/spectacles/get-started/introduction) — SIK, UI Kit, SyncKit | Build "Lenses" in Lens Studio (JS/TS). SIK = hand gestures (pinch/poke), UI Kit, SyncKit multiplayer, cloud + monetization. Full see-through AR + hand tracking. | See-through AR, hand tracking, spatial audio, fully standalone. Dev kit = Spectacles 5; consumer = Snap Specs. | Dev: $99/mo (1-yr); Specs ~$2,195 (Fall 2026) | 🟡 | 🔴 (AR / Lens Studio) |
| **Vuzix Z100 / M400** | Monocular HUD / enterprise glasses | ✅ [Vuzix SDK](https://support.vuzix.com/docs/developer-resources) (Android + iOS; camera APIs) | Full Android & iOS SDKs, Vuzix Connect demo apps, sample code. Z100 = notification/HUD display; M400 = Android wearable computer with camera/vision APIs. | Z100: 38g monochrome HUD, BT to phone. M400: camera, ruggedized Android, enterprise. | Z100 $499 (dev ed. $799); M400 ~$1,800 | 🟢 (Z100) | 🟡 (Android-based) |

---

## Watches / Smartwatches

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Apple Watch** (Series / Ultra) | Smartwatch | ✅ [watchOS SDK](https://developer.apple.com/watchos/) (Xcode) | Native on-device apps in Swift/SwiftUI. HealthKit (health/workout data), WorkoutKit, Core Motion, WatchConnectivity, complications, notifications. | HR, ECG, SpO₂, temp, GPS, fall/crash detect, cellular, rich apps. | ~$399+ (Series); Ultra ~$799 | 🟢 | 🟡 (Swift; needs Mac + Apple dev) |
| **Samsung Galaxy Watch** (+ Ultra) | Smartwatch (Wear OS) | ✅ [Wear OS SDK](https://developer.android.com/training/wearables) + [Samsung Health Sensor/Data SDK](https://developer.samsung.com/health/) | Wear OS apps (Kotlin/Compose). Samsung Health **Sensor SDK** = raw BioActive sensor data (Watch4+); **Data SDK** = integrated health data across watch/ring/phone. | HR, ECG, BIA body comp, sleep apnea, GPS, apps. | ~$300+; Ultra ~$650 | 🟢 | 🟡 (Wear OS / Kotlin) |
| **Garmin** (Forerunner / Fenix / etc.) | Sport / outdoor watch | ✅ [Connect IQ SDK](https://developer.garmin.com/connect-iq/) (Monkey C) | On-device apps in **Monkey C**: Watch Faces, Data Fields, Widgets, Device Apps, Audio providers. Sensor + ANT+ access; no garbage collector (predictable perf). | GPS, HR, multisport, maps, very long battery, big sensor set. | ~$200–1,000 | 🟢 | 🟡 (Monkey C, custom language) |
| **Amazfit** (Zepp OS) | Smartwatch | ✅ [Zepp OS SDK](https://developer.zepp.com/) (JavaScript) | On-device **Mini Programs** + watch faces in JS. Sensor access, UI framework, app store. Lightweight, easy entry. | HR, SpO₂, GPS, sleep, long battery, cheap. 200+ community mini apps. | ~$50–300 | 🟢 | 🟢 (JavaScript, low barrier) |

---

## Rings

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Even Realities R1** | Smart ring | ⚠️ No public ring SDK — controls G2 via Even ecosystem ([Even Hub](https://hub.evenrealities.com/)) | Not exposed directly. Acts as input (tap/press/scroll) for G2 glasses; health data via Even app. | Heart rate, HRV, SpO₂, temp, respiratory, sleep, steps; controls G2; IP68; ~4-day battery. | Not public yet (G2 companion) | 🟢 | ⚪ |
| **Aivela Ring Pro** | Smart ring | ❌ None announced | — | Multi-wavelength PPG, temp, 6-axis IMU, OFN touch surface. Sleep/HRV/stress/recovery, taps/swipes, AI insights, 7-day battery, IP68, titanium, subscription-free. | ~$149–179 early / $299 retail | 🟢 | ⚪ |
| **KiWear Ring** | Gesture-control ring | ⚠️ Planned/"exploring" — not yet available ([kiwear.com](https://www.kiwear.com/)) | Announced but no public API/SDK yet. | Air-mouse (cursor/click/drag/scroll), cross-device gesture control, health tracking, gesture gaming, waterproof. | ~$199 (KS) / $249 early bird | 🟢 | ⚪ (planned) |
| **Oura Ring 4** | Health smart ring | ✅ [Oura API v2](https://cloud.ouraring.com/v2/docs) (cloud REST, OAuth) | **Cloud** REST API (not on-device). Exposes sleep, readiness, HR, HRV, SpO₂, temp, activity, workouts. Free; apps over 10 users need approval. | Sleep/readiness/activity, temp trends, HR/HRV, ~7-day battery, titanium. | $349–499 + $5.99/mo membership | 🟢 | 🟢 (simple REST/OAuth) |
| **Samsung Galaxy Ring** | Health smart ring | ⚠️ Data-only via [Samsung Health Data SDK](https://developer.samsung.com/health/data/overview.html) | No on-device apps. Data SDK surfaces ring health data (sleep, HR, activity) into your app alongside watch/phone. | Sleep, HR, activity, ~7-day battery, IP68. Deep Samsung ecosystem. | ~$400 | 🟢 | 🟡 (Samsung Health only) |
| **Ultrahuman Ring Air** | Health smart ring | ✅ [UltraSignal / Partnership API](https://www.ultrahuman.com/ultrasignal/) (cloud REST, OAuth 2.0) | **Cloud** REST API by application. Exposes ring metrics, recovery, sleep, plus CGM data. Dev-kit loaner program. No subscription. | Sleep, HR/HRV, temp, movement; no subscription; light titanium. | $349 (no subscription) | 🟢 | 🟡 (must apply for API access) |

---

## Bands / Wristbands

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Mudra Link** | Neural (EMG) wristband | ✅ Mudra SDK / Mudra Studio — [API waitlist](https://mudra-band.com/pages/mudra-link-main) | Mudra Studio platform + API key (early access). Exposes neural/EMG gestures (7 customizable), fingertip pressure, air-touch, dual input (D-pad + pointer), real-time signal. For XR/glasses, gaming, navigation, accessibility. | EMG neural sensing, no camera needed, controls AR/VR + smart TV + desktop, lightweight. | $249 ($299 MSRP) | 🟡 | 🟡 (API-gated, neural input) |
| **Whoop 5.0** | Fitness strap (no screen) | ✅ [WHOOP API](https://developer.whoop.com/) (cloud REST, OAuth) | **Cloud** REST API (free to call). Exposes cycles, recovery, strain, sleep, workouts, HR. Developer and each end user need a membership. | Continuous HR, HRV, strain, recovery, sleep; screenless strap. | Membership from $199/yr (hardware included) | 🟢 | 🟢 (simple REST/OAuth) |
| **Fitbit** (Charge / Sense) | Fitness band / watch | ✅ [Fitbit Web API](https://dev.fitbit.com/) (cloud REST, OAuth; Google) | **Cloud** Web API only (on-device SDK retired). Exposes steps, HR, sleep, activity, SpO₂ (intraday needs approval). | HR, sleep, SpO₂, some GPS, steps. Google account. | ~$100–160 | 🟢 | 🟢 (REST; no on-device apps) |
| **Meta Neural Band** | EMG neural wristband | ✅ via [Meta Wearables Device Access Toolkit](https://developers.meta.com/wearables/) | EMG gesture input exposed to apps for Ray-Ban Display (pinch, swipe, subtle finger moves). Ships paired with the glasses. | Surface-EMG gesture control, no camera; drives the display glasses. | Bundled in $799 Ray-Ban Display | 🟢 | 🟡 (via Meta toolkit) |

---

## VR / MR Headsets (head-worn)

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Meta Quest 3 / 3S** | Standalone VR/MR headset | ✅ [Meta XR SDK](https://developers.meta.com/horizon/) (Unity/Unreal) + [OpenXR](https://developers.meta.com/horizon/downloads/package/oculus-openxr-mobile-sdk/) | Full XR stack via Presence Platform: hand/body tracking, color passthrough (MR), spatial anchors, scene understanding, controllers, eye/face (Pro). Unity, Unreal, native OpenXR, WebXR. | Color passthrough MR, 6DoF, hand tracking, big app store. | $299 (3S) / $499 (3) | 🟢 | 🟡 (Unity/Unreal, mature) |
| **Apple Vision Pro** | Spatial computer headset | ✅ [visionOS SDK](https://developer.apple.com/visionos/) (Xcode) | Native apps in Swift/SwiftUI + RealityKit + ARKit. Hand + eye tracking, scene reconstruction, spatial windows/volumes, shared space. | 4K-per-eye micro-OLED, eye + hand input, passthrough MR, M-series chip. | ~$3,499 | 🟡 | 🔴 (Apple-only, RealityKit) |

---

## Hearables (smart earbuds)

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Apple AirPods (Pro)** | Smart earbuds | ⚠️ Limited — [CMHeadphoneMotionManager](https://developer.apple.com/documentation/coremotion) / spatial audio APIs | No audio-stream SDK. You get head-tracking motion data (pitch/yaw/roll) and spatial-audio hooks from iOS. No custom on-device code. | ANC, spatial audio, head tracking, HR (some), hearing aid mode. | ~$179–249 | 🟢 | 🟡 (read-only motion; iOS gated) |

---

## Neuro / EEG headbands (brain-computer interface)

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Muse (2 / S)** | EEG headband | ✅ [Muse SDK](https://choosemuse.com/pages/developers) | Raw EEG, accelerometer/gyro, PPG (HR), and signal-quality data to your own mobile/desktop app. Also LSL streaming. | 4-channel EEG, meditation/sleep tracking, HR, movement. | ~$250–400 | 🟢 | 🟡 (EEG signal processing) |
| **Emotiv** (Insight / EPOC X) | EEG headset | ✅ [Cortex API](https://emotiv.gitbook.io/cortex-api) (JSON/WebSocket) | Real-time EEG streams, mental commands, facial expressions, motion, performance metrics. **Raw EEG needs a paid Premium license.** | 5–14 channel EEG, BCI mental commands, research-grade. | ~$299–999 | 🟡 | 🟡 (BCI; license for raw data) |

---

## AI wearables / lifeloggers

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Limitless Pendant** | Clip-on AI recorder | ✅ [Limitless Developer API](https://www.limitless.ai/developers) (REST, API key) | **Cloud** API: fetch lifelogs (transcripts) with search + pagination, get by ID, read chats. MCP server available. 180 req/min. | Always-on audio capture, transcription, AI memory/summaries. | ~$99–199 (⚠️ Meta acquired Dec 2025 — discontinued to new buyers) | 🟢 | 🟢 (simple REST + key) |

---

## Medical / CGM (continuous glucose)

| Device | Type | SDK? (link) | What the SDK exposes | Key capabilities | Price (USD) | Ease of use | Dev difficulty |
|---|---|---|---|---|---|---|---|
| **Dexcom G7** | Glucose sensor (CGM) | ✅ [Dexcom API v3](https://developer.dexcom.com/) (REST, OAuth 2.0) | **Cloud** API: glucose readings, trends, events, devices. ~1h delay (US). Sandbox with simulated data. Partner approval required. | Real-time continuous glucose, alerts, 10–15 day wear. | Prescription / pharmacy (varies) | 🟢 | 🟢 (REST/OAuth; approval + medical) |

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
- **Watches** have the most mature on-device SDKs: Apple Watch (watchOS), Samsung/Wear OS, Garmin (Connect IQ), Amazfit (Zepp OS, easiest — JavaScript).
- **VR/MR headsets** are the richest XR targets: Meta Quest (Unity/Unreal/OpenXR) is the most accessible; Vision Pro is powerful but Apple-locked.
- **Niche types with real SDKs:** EEG headbands (Muse, Emotiv), AI pendant (Limitless), glucose (Dexcom) — all mostly cloud/data APIs.
- **Most powerful / hardest:** XREAL Aura, Snap Spectacles, Rokid AR Studio, Vision Pro — full spatial computing (Unity / Lens Studio / Android XR / RealityKit).
- **Gesture / input SDKs:** Mudra Link and Meta Neural Band (EMG), plus hand-tracking on Snap and Rokid.
- **Rings are mostly closed for apps:** you get cloud health data (Oura, Ultrahuman) or nothing. No real on-device ring app platform yet.
- **No SDK yet:** Aivela Ring Pro, Even R1 (standalone), KiWear (planned).

---

## Sources

- Even Realities G2 — https://www.evenrealities.com/products/g2-a · Even Hub — https://hub.evenrealities.com/
- Even Realities R1 (ring) — https://www.evenrealities.com/smart-ring
- KiWear Ring — https://www.kickstarter.com/projects/kiwear/kiwear-ring-control-every-device-with-a-gesture · https://www.kiwear.com/
- Aivela Ring Pro — https://www.aivela.com/pages/aivela-ring-pro
- XREAL Aura — https://www.xreal.com/us/aura
- Mudra Link — https://mudra-band.com/pages/mudra-link-main
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
- Amazfit / Zepp OS — https://developer.zepp.com/
- Meta Quest / Horizon SDK — https://developers.meta.com/horizon/ · OpenXR — https://developers.meta.com/horizon/downloads/package/oculus-openxr-mobile-sdk/
- Apple visionOS — https://developer.apple.com/visionos/
- Apple Core Motion (AirPods) — https://developer.apple.com/documentation/coremotion
- Muse SDK — https://choosemuse.com/pages/developers
- Emotiv Cortex API — https://emotiv.gitbook.io/cortex-api
- Limitless developer API — https://www.limitless.ai/developers
- Dexcom developer API — https://developer.dexcom.com/
- XR resource list — https://github.com/seckincengiz/XR
