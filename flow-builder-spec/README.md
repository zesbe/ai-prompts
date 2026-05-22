# Visual Flow Builder Spec — hallowa.id

Prompt untuk susun **technical spec + UX design** Visual Flow Builder (chatbot drag-drop) di hallowa.id. Ship Q1 2026, MVP 8 minggu, full feature 12 minggu.

## 🎯 Why This Matters

Per [feature gap analysis](../feature-gap-analysis/), Visual Flow Builder = **gap kritis #1** (deal-breaker untuk B2B serious). Kompetitor wajib punya: Qontak ✓, Qiscus AgentLabs ✓, SleekFlow ✓, Wati ✓. Hallowa ✗.

## 📊 Research Findings 2026

| Tech Option | Pros | Cons |
|---|---|---|
| **React Flow** | Open-source, popular, big community | License untuk Pro features |
| **Visual Flow** | SaaS-proof, scalable | Newer, smaller community |
| **JointJS** | Enterprise-grade | Steep learning curve |
| **Stately.ai** | State machine native | Paradigm shift untuk team |
| Custom canvas | Full control | 6-12 months extra effort |

**Recommendation:** React Flow untuk MVP (proven, fast ship), evaluate ulang at scale.

## 📋 Coverage

- Product spec dengan user stories per persona
- Node types (trigger, send, logic, action, integration, end)
- UX flow (onboarding, canvas, config panel, test mode, publish)
- Data model + API design (REST + WebSocket)
- Edge cases & error handling
- Analytics & monitoring
- 12-week rollout plan
- Competitor deep-dive (Qontak, Qiscus, SleekFlow, Wati, Landbot)

## 🚀 Cara Pakai

1. Buka [`prompt.txt`](./prompt.txt)
2. Copy raw → paste ke AI assistant
3. Mulai dari product spec → competitor analysis → architecture → roadmap

## 📝 Catatan

- **2026-05-22** — Initial version
