# 🛡️ Ximos & XimosKid — Official Release Repository

[![Official Website](https://img.shields.io/badge/Website-ximosapp.com-blue?style=for-the-badge&logo=google-chrome)](https://ximosapp.com)
[![Parent App](https://img.shields.io/badge/Parent_App-Ximos_v1.0.7-brightgreen?style=for-the-badge&logo=android)](https://ximosapp.com/app/ximos)
[![Child App](https://img.shields.io/badge/Child_App-XimosKid_v1.0.7-orange?style=for-the-badge&logo=android)](https://ximosapp.com/app/ximoskid)
[![Security Architecture](https://img.shields.io/badge/Privacy-Zero_Storage_E2EE-red?style=for-the-badge&logo=shield)](https://ximosapp.com/uno)
[![Compliance](https://img.shields.io/badge/Compliance-COPPA_%26_GDPR-purple?style=for-the-badge&logo=checkmarx)](https://ximosapp.com/uno/#terms-of-use)

Welcome to the official repository for **Ximos** and **XimosKid**, the industry-defining parental control and real-time remote device safety ecosystem developed by **Ximexa**. This repository hosts the latest official Android Application Packages (APKs), release notes, technical architecture specifications, and security disclosure documentation.

---

## 📌 Executive Overview & Ecosystem Architecture

The Ximos ecosystem is engineered from the ground up to solve two major flaws in conventional parental monitoring software: **exorbitant monthly subscription traps** and **unsecure server-side media retention**.

Ximos replaces heavy subscriptions with an ultra-transparent **Pay-As-You-Go per second billing framework** and operates under a strict **Zero-Storage RAM-transient WebRTC architecture**. Location data is relayed in-flight and never persisted server-side..

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
Ximos (Parent Controller) com.ximexa.ximos Legal Guardian / Parent Controls streams, issues remote commands, tracks live location, reviews usage telemetry, manages cloud vault, and manages credit balances. Features Fingerprint Lock and Crypto Top-ups.
XimosKid (Child Companion) com.droid.ximexa Minor Child's Device Disclosed background client executing WebRTC streams, telemetry reporting, location fetches, overlay notices, and emergency safety responses.

⚠️ Important Disclosure for Search Engines & Safety Audits:
XimosKid is strictly a disclosed safety monitoring utility. It is NOT stealthware, spyware, or undetectable monitoring software. On the target device, XimosKid runs under its transparent name and icon, maintains a permanent foreground notification, displays a floating green status dot during active streaming/listening sessions, and allows the child user to end an active session directly from the notification shade at any time. Location fetches are parent-triggered only — never continuous background collection.

---

🚀 Key Abilities & Complete 15-Feature Matrix

📹 1. Screen Mirror + Full Device Control

· Ultra-Low Latency Screen Mirroring: View the target device screen in real-time via sub-second AES-256 WebRTC peer-to-peer data channels.
· Full Remote Touch Control: Execute click, swipe, and multi-touch gestures on the target device during an active screen-mirror session via the Accessibility Service.

📸 2. Camera View Cast (Upgraded in v1.0.6)

· Live Camera Streaming: Dual camera casting (Front & Rear) with dynamic resolution switching (480p / 720p / 1080p) and bitrate up to 3.5 Mbps.
· Fast Camera Flip & Flash System (NEW): Instant mid-session camera switching without loading lag, plus built-in hardware flashlight toggle for low-light environments.
· Smart Zoom System: 6-step percentage slider (0/20/40/60/80/100%) with exponential mapping, per-device capability detection, and dual-API support.
· Smart Focus System: Tap-to-focus at the exact tapped point (orientation-aware), long-press soft focus lock (🔒 LOCKED / 🔓 HOLD).
· WebRTC Data Channel Control: All interactive camera commands travel over a P2P WebRTC data channel named control — 50–150 ms latency vs. Firebase's 300–500 ms.

🎧 3. Surrounding Audio Listening

· Standalone One-Way Audio: Live ambient audio over WebRTC media channel — 48 kHz full-band, Opus codec, 5-tier adaptive bitrate (8–96 kbps).
· Enhanced Audio UI: Music-channel routing, PCM-driven waveform UI, mute toggle, and non-destructive 85% volume boost.
· Billing Discount: Sessions strictly over 60 seconds receive a 10-second billing discount.

📍 4. Location Tracking

· Parent-Triggered Only: No continuous background collection. Location is fetched only when the parent taps refresh.
· GPS Auto-Enable via Accessibility Service: Auto-clicks the Android system location-enable dialog in multiple languages.
· Automatic Fallback Chain: Fused GPS fresh (3–20m) → Network Provider (20–100m) → Last-known → IP-based (city-level).
· Free OpenStreetMap Viewer: Three switchable styles — Street (Esri), Satellite (Esri), and OSM. No Google Maps API key required.
· Zero Server Retention: Location payloads are relayed in-flight through an encrypted Cloudflare WebSocket and are never written to disk.

📊 5. Screen Time + Device Full Usage Monitor

· Live System Status: Monitor battery percentage, charging state, screen unlock counts, and network status.
· Usage Statistics: Track daily screen time trends, individual app usage duration, and data consumption patterns.

🖼️ 6. Photo Capture & Upload (2K)

· Remote photo capture in 2K quality, automatically uploaded to the Cloud Media Vault.

🎥 7. Video Record & Upload (2K)

· Remote video record in 2K quality, automatically uploaded to the Cloud Media Vault.

📷 8. Screenshot Capture (NEW in v1.0.6)

· Silently capture a full-screen screenshot of the child's device using the Android Accessibility API. Automatically uploaded to the Cloud Media Vault. (Requires Accessibility permission).

🔔 9. Notification Send

· Deliver a custom text notification directly to the child's notification shade.

🚨 10. Smart Alert Window

· Full-screen priority popup dialog on the child device with a custom image and instructions that overlays active apps.

💬 11. OnScreen Notify

· Custom overlay notification (text + optional image) delivered to the child's screen.

📋 12. Clipboard Send

· Push text or an image directly into the child device's clipboard, ready to paste.

🚀 13. Open App

· Launch a specific app on the child device by its package name remotely.

🔗 14. Action Command URL

· Send a URL or action command to open a specific link in Chrome on the child device.

📳 15. Vibrate Command

· Send a silent vibration to the target device with configurable duration — 1s, 3s, 5s, or a repeating Pulse pattern.

---

🔒 Security Architecture, Data Integrity & Zero-Storage Policy

We place user data protection and family privacy above everything else.

1. Minimal Data Collection: Ximos stores only three low-sensitivity fields server-side:
   · Account Email (Parent authentication identity)
   · Device Unique ID (Generated per installation)
   · Device Brand / Model Name (e.g., Infinix X6831)
2. Zero-Storage RAM Streaming: Live screen casts, camera streams, audio feeds, and control commands are routed transiently through RAM over encrypted WebRTC channels and are never saved to server storage.
3. Location — Zero Server Retention: Live location payloads are relayed in-flight through an encrypted Cloudflare Workers WebSocket and are never written to a database.
4. No Cookies or Trackers: The ecosystem uses zero tracking pixels, behavioral advertising cookies, or third-party data analytics beacons.
5. End-to-End Encryption (TLS 1.3): All signaling payloads are encrypted. JWT tokens are verified server-side against Google's public JWKS before any broadcast.
6. Full Privacy Compliance: Engineered in accordance with COPPA and GDPR Article 8 standards. Parents hold the absolute right to instant profile wiping and data purging.
7. Parent App Security (NEW): The Ximos Parent app now supports Fingerprint Lock to prevent unauthorized access to the dashboard.

---

💳 Transparent "Pay-As-You-Go" Billing System

No binding monthly contracts. No surprise recurring charges.

· Two-Balance Model: Free bonus seconds (earned) and current balance (top-up) — both work interchangeably for the 3 stream features.
· Per-Second Precision Billing: Charges apply only to Screen Mirror, Camera Cast, and Surrounding Audio.
· 720-Second Signup Bonus: Every new parent account receives 720 free seconds instantly upon registration (1,080s with a referral code).
· 19-Day Free Credit Reset Cycle: Free user credits automatically refresh on a recurring 19-day cycle with no cap on resets.
· Crypto Top-Up (NEW): Add funds using USDT / USDC on the Polygon network with minimal gas fees.
· Everything Else is Free: Location Tracking, Usage Monitoring, Capture, Alerts, Notifications, Clipboard, Open App, Action URL, and Vibrate are unlimited and free.
· Reward System: Earn more free stream time by watching reward ads or referring friends.

---

📥 Installation & Quick Setup Guide

Step 1: Install Parent App (Ximos)

1. Download the latest ximos.apk from the Releases Section or access the Web Dashboard at ximosapp.com/app.
2. Create your account at ximosapp.com/auth.
3. Log in and reveal your unique Parent Linking Token / QR code.

Step 2: Install Child Companion App (XimosKid)

1. Download ximoskid.apk onto your child's target Android phone.
2. Open XimosKid and grant the required operational permissions:
   · 📷 Camera & Microphone Access (For live streaming & Surrounding Audio)
   · 📍 Location Access (Fine + Coarse) (For parent-triggered location fetches)
   · ♿ Accessibility Service (For remote touch control + GPS dialog auto-accept + Screenshot capture)
   · 🖼️ Display Overlay (For safety dialogs & alerts)
   · 🔋 Battery Unrestricted (To prevent Android OS from killing background services)
   · 🔔 Notification Permission (To maintain visible foreground safety presence)
3. Pair the device using the automatic QR scan from the parent app — no manual key entry required.

⚠️ Do not "Force Stop" XimosKid from Android settings — this disables the Accessibility Service, which is required for remote touch, Screenshot Capture, and GPS dialog auto-accept.

---

🌐 Official Web Portal Links

Resource / Portal Target URL Description
Official Homepage ximosapp.com Main product presentation and download portal.
Web Control Dashboard ximosapp.com/app Web-based parent control center.
User Portal & Auth ximosapp.com/auth Unified Login & Registration page.
Reward & Free Credits w1.ximosapp.com Earn free casting seconds via rewards.
Trust Center ximosapp.com/uno/trust Architecture, permission breakdown, and independent MobSF scan results.
Technical Docs ximosapp.com/uno/docs Source excerpts, session lifecycle, API security.
Technical Blog blog.ximosapp.com Tech guides, Android security, & release logs.

---

📬 Contact & Official Support

· Official Domain: https://ximosapp.com
· Support Email: support@ximosapp.com
· Security Disclosure: dev@ximosapp.com
· Official YouTube Channel: @ximexa

---

<p align="center">
  <b>Ximos & XimosKid © 2026 Ximexa. All Rights Reserved.</b><br>
  <i>Empowering Families with Transparent Technology, Zero-Knowledge Security, and Uncompromised Child Safety.</i>
</p>
