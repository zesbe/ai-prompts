# Mobile App Development Plan — hallowa.id

Prompt untuk susun mobile app dev plan hallowa.id (iOS + Android) untuk **agent CS yang kerja dari mana saja**. Ship MVP 12-16 minggu.

## 🎯 Why This Matters

Per [feature gap analysis](../feature-gap-analysis/), mobile app = critical gap. Agent CS UMKM Indonesia gak duduk depan PC seharian. Kompetitor (Qontak, Qiscus, SleekFlow) udah punya native app.

## 📊 Research Findings 2026

| Framework | Market Share | Best For |
|---|---|---|
| **Flutter** | 46% | Performance, UI consistency, single codebase clean |
| **React Native** | 35-42% | Hiring di Indonesia, web reuse, ecosystem |
| **Native** | (premium) | Best perf, full platform features, 2x cost |
| Capacitor/Ionic | (low) | Web-first wrapper, MVP only |
| KMM | (emerging) | Kotlin enthusiast, future-proof bet |

**Likely recommendation untuk hallowa:** React Native + Expo (kalau tim udah pake React di web), atau Flutter (kalau prioritas performance).

## 📋 Scope

- Tech stack decision (5 opsi dengan trade-off)
- MVP scope (Phase 1: 9 must-have, Phase 2: 8 nice-to-have)
- Push notification strategy (FCM, APNs, OneSignal)
- Authentication & security (biometric, JWT, certificate pinning)
- Offline-first strategy (outbox pattern, conflict resolution)
- Performance targets (size <30MB, cold start <2s)
- UI/UX design principles (platform native, accessibility, dark mode)
- Architecture (state mgmt, real-time, image, navigation)
- Release strategy (TestFlight, phased rollout)
- ASO (App Store Optimization)
- CI/CD pipeline
- 16-week roadmap

## 💰 Budget Indikasi

- Team: 2 mobile dev + 1 backend + 0.5 designer + 0.5 PM
- Duration: 12-16 minggu MVP
- Total estimasi: **Rp 200-500jt all-in**

## 🚀 Cara Pakai

1. Buka [`prompt.txt`](./prompt.txt)
2. Copy raw → paste ke AI assistant
3. Mulai dari tech stack decision

## 📝 Catatan

- **2026-05-22** — Initial version
