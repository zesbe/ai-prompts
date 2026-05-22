# Marketplace Integration — hallowa.id

Prompt untuk riset & design integration plan hallowa.id ke **Tokopedia, Shopee, Lazada, TikTok Shop**. Goal: jadi moat Indonesia yang sulit di-copy global player.

## 🎯 Why This Matters

UMKM Indonesia jualan di marketplace (Shopee, Tokopedia paling dominan). Hallowa cuma cover Meta channels. Tanpa marketplace integration, hallowa kalah ke Qiscus (20+ app integration).

## ⚠️ CRITICAL FINDING

Per dokumentasi Yellow.ai (sumber resmi):

> **Shopee chatbot replies are NOT supported.** Recommended: live agent only.

Ini constraint kunci. Hallowa harus design feature sebagai **unified inbox** (agent inbox), bukan auto-reply otomatis untuk Shopee.

## 📊 Marketplace Comparison

| Marketplace | API Status | Chat API | Bot Allowed | Onboarding |
|---|---|---|---|---|
| Tokopedia | Open API exists | Partial | Need check | Apply partner |
| Shopee | Open Platform | Yes (read+send) | ❌ Live agent only | Apply Open Platform |
| Lazada | Open Platform | Yes | Partial | Developer registration |
| TikTok Shop | Partner Center | Limited | Mixed | Partner application |

## 📋 Scope

- API & feasibility audit per marketplace
- Partnership pathway (apply process, timeline, cost)
- Legal & compliance (PDP UU 27/2022)
- Integration architecture (direct vs aggregator)
- MVP scope per marketplace (3 phases)
- Data model addition
- Backend complexity estimate
- Rollout prioritization
- Alternative: partner with Anchanto/AccelByte vs build

## 💰 Budget Indikasi

- Partner fees: gratis–$2000/year per marketplace
- Aggregator fee (kalau pakai): $500-3000/month
- Development: 1 backend + 0.5 frontend × 8-12 minggu
- Total estimasi: **Rp 100-300jt all-in untuk MVP** (cover 2 marketplace)

## ⏱️ Timing

- Riset: 1-2 minggu
- Partner application: 4-12 minggu (parallel)
- MVP development: 8-12 minggu setelah API approved
- **Total realistic: 4-6 bulan untuk MVP cover 2 marketplace**

## 🚀 Cara Pakai

1. Buka [`prompt.txt`](./prompt.txt)
2. Copy raw → paste ke AI assistant
3. Mulai dari API feasibility (paling kritis)

## 📝 Catatan

- **2026-05-22** — Initial version
- Re-check setiap kuartal (marketplace API berubah cepat)
