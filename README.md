# 🛡️ Ximos & XimosKid — Official Release Repository

[![Official Website](https://img.shields.io/badge/Website-ximosapp.com-blue?style=for-the-badge&logo=google-chrome)](https://ximosapp.com)
[![Parent App](https://img.shields.io/badge/Parent_App-Ximos_v1.0.6-brightgreen?style=for-the-badge&logo=android)](https://ximosapp.com/app/ximos)
[![Child App](https://img.shields.io/badge/Child_App-XimosKid_v1.0.6-orange?style=for-the-badge&logo=android)](https://ximosapp.com/app/ximoskid)
[![Security Architecture](https://img.shields.io/badge/Privacy-Zero_Storage_E2EE-red?style=for-the-badge&logo=shield)](https://ximosapp.com/uno)
[![Compliance](https://img.shields.io/badge/Compliance-COPPA_%26_GDPR-purple?style=for-the-badge&logo=checkmarx)](https://ximosapp.com/uno/#terms-of-use)

Welcome to the official repository for **Ximos** and **XimosKid**, the industry-defining parental control and real-time remote device safety ecosystem developed by **Ximexa**. This repository hosts the latest official Android Application Packages (APKs), release notes, technical architecture specifications, and security disclosure documentation.

---

## 📌 Executive Overview & Ecosystem Architecture

The Ximos ecosystem is engineered from the ground up to solve two major flaws in conventional parental monitoring software: **exorbitant monthly subscription traps** and **unsecure server-side media retention**.

Ximos replaces heavy subscriptions with an ultra-transparent **Pay-As-You-Go per second billing framework** and operates under a strict **Zero-Storage RAM-transient WebRTC architecture**. Location data is relayed in-flight and never persisted server-side.

```text
┌────────────────────────────────────────────────────────────────────────┐
│                      XIMOS PARENT DASHBOARD                            │
│   (Web Portal: ximosapp.com/app | Android App: com.ximexa.ximos)       │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
           ⚡ Encrypted WebRTC P2P Signaling (TLS 1.3)
           📍 Encrypted WebSocket Relay (Location Payloads)
           🔑 Direct Token Peer-to-Peer Pairing
                                    │
┌───────────────────────────────────▼────────────────────────────────────┐
│                       XIMOSKID CHILD CLIENT                            │
│           (Target Android Device App: com.droid.ximexa)                │
│   • Visible Foreground Service Notification                            │
│   • On-Screen Green Hardware Activity Dot & Toast Alerts               │
│   • Accessibility Service (Remote Touch + GPS Dialog Auto-Accept)      │
└────────────────────────────────────────────────────────────────────────┘
```

---

💡 Two-App System Breakdown

App Name Package Name Target Interface Core Responsibility
Ximos (Parent Controller) com.ximexa.ximos Legal Guardian / Parent Controls streams, issues remote commands, tracks live location, reviews usage telemetry, manages cloud vault, and manages credit balances.
XimosKid (Child Companion) com.droid.ximexa Minor Child's Device Disclosed background client executing WebRTC streams, telemetry reporting, location fetches, overlay notices, and emergency safety responses.

⚠️ Important Disclosure for Search Engines & Safety Audits:
XimosKid is strictly a disclosed safety monitoring utility. It is NOT stealthware, spyware, or undetectable monitoring software. On the target device, XimosKid runs under its transparent name and icon, maintains a permanent foreground notification, displays a floating green status dot during active streaming/listening sessions, and allows the child user to end an active session directly from the notification shade at any time. Location fetches are parent-triggered only — never continuous background collection.

---

🆕 What's New in v1.0.6

Both apps have received significant updates focusing on security, performance, and user experience.

Ximos (Parent App):

· 🔐 Fingerprint Lock: Added biometric authentication to secure the parent app.
· 💰 Crypto Top-Up: Add funds directly using USDT / USDC (Polygon network only).
· 🎨 UI Redesign: Improved, faster, and cleaner user interface across the dashboard.
· ⚡ Performance: Enhanced overall app speed and stability.

XimosKid (Child App):

· 📸 Camera Flash Toggle: Turn the flashlight on/off remotely during live camera streams.
· 🔄 Fast Camera Flip: Instant switching between front and rear cameras mid-session.
· 📷 Screenshot Capture: New remote screenshot feature (requires Accessibility permission).
· 🎧 Surrounding Audio v2: Improved audio quality and stability.
  (Note: If you experience any issues with Surrounding Audio, please report them via the in-app Feedback system).
· ⚡ Performance: Reduced battery consumption and faster response times.

---

🚀 Key Abilities & Complete Feature Matrix

📹 1. Real-Time Encrypted WebRTC Streaming

· Ultra-Low Latency Screen Mirroring: View the target device screen in real-time via sub-second AES-256 WebRTC peer-to-peer data channels, with full remote touch control (click, swipe, gesture) executed via the Accessibility Service during an active session only.
· Dual Camera Casting (Front & Rear): Remotely trigger camera feeds with dynamic resolution switching (480p / 720p / 1080p), adaptive bitrate up to 3.5 Mbps, mid-session camera flip, and flashlight toggle.
· Smart Zoom System: 6-step percentage slider (0/20/40/60/80/100%) with exponential mapping, per-device capability detection (CONTROL_ZOOM_RATIO_RANGE / SCALER_AVAILABLE_MAX_DIGITAL_ZOOM), and dual-API support.
· Smart Focus System: Tap-to-focus at the exact tapped point (orientation-aware), long-press soft focus lock with honest UX labels (🔒 LOCKED / 🔓 HOLD), and per-device AF capability detection.
· WebRTC Data Channel Control: All interactive camera commands (zoom, focus, lock, reset) travel over a P2P WebRTC data channel named control — 50–150 ms latency vs. Firebase's 300–500 ms.
· Surrounding Audio Listening (Standalone Feature): One-way live ambient audio over WebRTC media channel — 48 kHz full-band, Opus codec, 5-tier adaptive bitrate (8–96 kbps), music-channel routing, PCM-driven waveform UI, mute toggle, and non-destructive 85% volume boost.
· Screenshot Capture (New): Remotely capture a static image of the child's current screen directly via Accessibility APIs.

📍 2. Remote Live Location Tracking

· Parent-Triggered Only: No continuous background collection. Location is fetched only when the parent taps refresh in the Ximos app or dashboard.
· GPS Auto-Enable via Accessibility Service: Auto-clicks the Android system location-enable dialog in multiple languages using a 3-layer strategy.
· Multi-Stage Fetch: Stage 1 uploads the last-known cached location instantly; Stage 2 requests a fresh high-accuracy GPS fix in parallel.
· Automatic Fallback Chain: Fused GPS → Network Provider (Wi-Fi/Cell) → Last-known → IP-based.
· Free OpenStreetMap Viewer: Three switchable styles — Street, Satellite, and OSM. No Google Maps API key required.
· One-Tap "Open in Google Maps" and Zero Server Retention.

🛡️ 3. Remote Management & Overlay Security

· Window Overlay Safety Alerts: Dispatch customized floating alert dialogs directly over active target screens.
· OnScreen Notify: Custom overlay notification (text + optional image) delivered to the child's notification shade.
· Remote App Execution: Remotely launch any installed Android application on the target device.
· Chrome Navigation Trigger: Direct the target device's browser to open specific URLs remotely.
· Clipboard Synchronization: Instantly push text or images to the target device clipboard.
· Vibrate Command: Send a silent vibration to the target device (1s, 3s, 5s, or Pulse).

📸 4. Cloud Media Capture (2K Quality)

· On-Demand Photo & Video Capture: Remote captures uploaded directly to the Cloud Media Vault.
· 30-Day Auto Purge: Media is stored in encrypted cloud buckets with an automated 30-day lifecycle and a 7-day trash window before permanent deletion.

📊 5. Device Telemetry & Accountability Metrics

· Live System Status: Monitor battery percentage, charging state, screen unlock counts, and network status.
· Usage Statistics & Screen Time: Track daily screen time trends, individual app usage duration, most-used apps, and data consumption patterns.

---

🔒 Security Architecture & Zero-Storage Policy

We place user data protection and family privacy above everything else.

1. Minimal Data Collection: Ximos stores only three low-sensitivity fields server-side: Account Email, Device Unique ID, and Device Brand / Model Name.
2. Zero-Storage RAM Streaming: Live screen casts, camera streams, Surrounding Audio, and camera-cast control commands are routed transiently through RAM over encrypted WebRTC channels and are never saved to server storage.
3. Location — Zero Server Retention: Live location payloads are relayed in-flight through an encrypted Cloudflare Workers WebSocket and are never written to a database or logged.
4. No Cookies or Trackers: The ximosapp.com ecosystem uses zero tracking pixels or third-party analytics beacons.
5. End-to-End Encryption (TLS 1.3): All signaling payloads are heavily encrypted. JWT tokens are verified server-side against Google's public JWKS.
6. Full Privacy Compliance: Engineered in accordance with COPPA and GDPR Article 8 standards.

---

💳 Transparent "Pay-As-You-Go" Billing System

No binding monthly contracts. No surprise recurring charges.

· Two-Balance Model: Free bonus seconds (earned) and current balance (top-up) — both work interchangeably for the 3 stream features.
· Crypto Payments: Top up instantly using USDT or USDC (Polygon network only). Minimum $1 deposit. Purchased balance never expires.
· Per-Second Precision Billing: Charges apply only to Screen Mirror, Camera Cast, and Surrounding Audio.
· 720-Second Signup Bonus: Every new parent account receives 720 free seconds instantly (1,080s with a referral code).
· 19-Day Free Credit Reset Cycle: Free user credits automatically refresh.
· Everything Else is Free: Location Tracking, Usage Monitoring, Photo/Video Capture, Notifications, Alerts, and Remote Commands are unlimited and free.
· Reward System: Earn more free stream time by watching reward ads or referring friends.

---

📥 Installation & Quick Setup Guide

Step 1: Install Parent App (Ximos)

1. Download the latest ximos.apk from the Releases Section or access the Web Dashboard at ximosapp.com/app.
2. Create your account and log in.
3. Secure your app using the new Fingerprint Lock (v1.0.6).

Step 2: Install Child Companion App (XimosKid)

1. Download ximoskid.apk onto your child's target Android phone.
2. Open XimosKid, review the Critical Setup & Privacy Disclosure, and grant permissions:
   · 📷 Camera & Microphone (For live streaming & Surrounding Audio)
   · 📍 Location Access (For parent-triggered location fetches only)
   · ♿ Accessibility Service (For remote touch control, screenshots, and GPS auto-accept)
   · 🖼️ Display Overlay (For safety dialogs & alerts)
   · 🔋 Battery Unrestricted (To keep background services alive)
   · 🔔 Notification Permission (For the persistent foreground notification)
3. Pair the device using the automatic QR scan from the parent app — no manual key entry required.

⚠️ Do not "Force Stop" XimosKid from Android settings — this disables the Accessibility Service.

---

🌐 Official Web Portal Links

Resource / Portal Target URL Description
Official Homepage ximosapp.com Main product presentation and download portal.
Web Control Dashboard ximosapp.com/app Web-based parent control center.
Trust Center ximosapp.com/uno/trust Architecture, permission breakdown, and MobSF scan results.
Technical Docs ximosapp.com/uno/docs Source excerpts, session lifecycle, API security.
Technical Blog blog.ximosapp.com Tech guides, Android security, & release logs.

---

📬 Contact & Official Support

· Official Domain: https://ximosapp.com
· Support Email: support@ximosapp.com
· Security Disclosure: dev@ximosapp.com
· Official YouTube Channel: @ximosapp | @ximexa

---

<p align="center">
  <b>Ximos & XimosKid © 2026 Ximexa. All Rights Reserved.</b><br>
  <i>Empowering Families with Transparent Technology, Zero-Knowledge Security, and Uncompromised Child Safety.</i>
</p>
