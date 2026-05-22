# Iklan FB Ads — hallowa.id (v2)

Prompt komprehensif untuk setup Facebook Ads campaign untuk **hallowa.id** berbasis **data benchmark 2026** dan best practices terbaru: CAPI, Advantage+ hybrid, creative-first, iOS 14+ ready.

> ⚠️ **v2 update (2026-05-22)**: Direvisi setelah riset 2026. v1 awal kurang cover CAPI, Advantage+, creative testing methodology, dan punya estimasi CPL terlalu optimis untuk B2B SaaS.

## 📊 Data Benchmark 2026 (yang dipakai di prompt)

| Metric | Value 2026 | Source |
|---|---|---|
| B2B SaaS CPL (global) | $50-150 USD (Rp 750k-2.25jt) | saashero.net |
| SaaS CPL trend YoY | +109% (2025-2026) | superads.ai |
| CPM Indonesia (estimasi tier-2) | $2-5 (vs US $23) | adamigo.ai |
| **CPL B2B SaaS Indonesia (realistic)** | **Rp 300k-800k** | derivasi |
| Target CTR B2B SaaS | 0.5-1% (elite 1.5%+) | saashero.net |
| Target CPC B2B SaaS | $2-5 (Rp 30-75k) | saashero.net |
| Conversion rate FB B2B | 10.63% blended | saashero.net |
| ROAS minimum profit | 4-6x | saashero.net |
| Pixel-only miss conversion | 50%+ post-iOS 14 | dataally.ai |
| **Creative quality % of performance** | **70%** | Meta internal |
| Advantage+ vs detailed CPA | -32% lower | Meta internal |
| Lead response <5min vs 30min | 21x more conversion | leadsync.me |
| Attribution window B2B | 90 hari | saashero.net |

## ⚠️ Kenapa Pixel-Only Setup Gak Cukup di 2026

iOS 14+ dan privacy updates browser (Safari ITP, Chrome 3rd party cookie deprecation) **menghancurkan akurasi browser-side tracking**. Realitas 2026:

- ❌ Pixel-only setup miss **50%+** conversion
- ❌ 90% B2B teams setup CAPI **salah** (EMQ score <5 = data sampah)
- ✅ **CAPI (server-side) wajib** untuk akurasi
- ✅ Event deduplication browser + server (event_id matching)
- ✅ Target EMQ score minimum 6/10 (ideal 8+)

## 🎯 Konteks Bisnis

| Aspek | Detail |
|---|---|
| Produk | SaaS unified messaging platform B2B |
| Status | Official Meta Business Partner |
| Integrasi | WhatsApp Business API, Instagram, Messenger, Threads |
| Target | UMKM sampai enterprise di Indonesia |
| Pricing | Free / Starter Rp199k / Pro Rp599k / Enterprise |
| Trial | 14 hari semua paket berbayar |
| Kompetitor | Mekari Qontak, Qiscus, Wati.io, YCloud |

## 💰 Campaign Parameters

| Parameter | Value |
|---|---|
| Objective | Lead Generation / Trial Signup |
| Budget harian | Rp 100.000 |
| Durasi | 30 hari |
| Total budget | Rp 3.000.000 |
| Landing page | https://app.hallowa.id/register |

## 📈 Estimasi Realistic (Updated dengan data 2026)

Dengan budget Rp 3jt dan CPL B2B SaaS Indonesia Rp 300k-800k:

| Metric | Estimasi 30 hari |
|---|---|
| Lead total | 4-10 |
| Trial signup | 1-3 |
| Paying customer | 0-1 (bulan 1) |
| Profitability decision | Bulan 4-6 |

**Bulan 1 = "data collection phase".** Fokus bukan immediate ROAS, tapi:
- Bersihin infrastruktur tracking (CAPI proper, EMQ 6+)
- Test creative angle
- Identify winning audience
- Build retargeting pool

## 🏗️ Struktur Campaign (3 Opsi)

### Opsi A — Hybrid Modern (REKOMENDASI default)
- 1 Campaign (Sales/Conversions)
- 2 Ad Sets:
  - Advantage+ Audience: Rp 60k/hari (broad, AI-driven)
  - Detailed Targeting: Rp 40k/hari (cold prospecting)
- 3 Ads per Ad Set (creative testing)

### Opsi B — Pure Manual
Kalau Pixel/CAPI belum mature untuk Advantage+.

### Opsi C — Funnel-Based
Cold + Warm + Hot retargeting (kalau udah ada audience data).

AI bakal kasih recommendation berdasarkan status infrastruktur.

## 🎨 Creative Strategy (KRUSIAL — 70% Performance)

Riset 2026 nunjukin **70% variance performance ditentukan creative**. Bukan targeting. Prompt ini push hard di creative testing:

- **3+ format** (image, carousel, video 15-30s)
- **3+ angle** (pain, solution, proof, authority, FOMO)
- **Aspect ratios wajib**: 1:1, 4:5, 9:16

## ✅ Pre-flight Checklist

- [ ] Chrome udah terbuka, akun FB & BM udah login
- [ ] Payment method aktif & cukup buffer untuk Rp 3jt+
- [ ] Domain hallowa.id udah verified di Business Manager
- [ ] **Meta Pixel** udah terpasang di hallowa.id (+ test fired)
- [ ] **CAPI / Conversions API** udah setup (kritis 2026!)
  - Cara cepat: CAPI Gateway Meta
  - Lebih advanced: Stape, Segment, Wzrd, custom server-side
- [ ] **EMQ score** minimum 6/10 untuk semua events
- [ ] 8 prioritized events di-set di Aggregated Event Measurement
- [ ] Custom audiences udah di-setup (visitor, pricing page, dll)
- [ ] Lookalike audience kalau ada ≥1000 customer data
- [ ] Privacy policy & cookie consent udah live di hallowa.id
- [ ] **Sales team / CS team siap respond <5 menit** ke lead inquiry
  (lead response <5 min = 21x conversion vs >30 min)

## 🚀 Cara Pakai

1. Buka [`prompt.txt`](./prompt.txt)
2. Klik tombol **Raw** atau **Copy raw file**
3. `Ctrl+A` → `Ctrl+C`
4. Buka sesi AI assistant baru (context bersih)
5. Paste sebagai pesan pertama

## 🔒 Mode Keamanan

- ✅ Mulai dari **infrastructure audit**, JANGAN langsung buat campaign
- ✅ Phase 1 wajib selesai (Pixel + CAPI healthy) sebelum Phase 2
- ✅ Tiap phase butuh approval sebelum lanjut
- ❌ AI **tidak boleh** auto-publish
- ❌ User yang klik "Publish Campaign"
- ❌ User yang verify payment method

## 📋 6-Phase Workflow

| Phase | Fokus | Deliverable |
|---|---|---|
| 1 | Infrastructure audit | Pixel + CAPI status report, fix list |
| 2 | Campaign structure | Proposal Opsi A/B/C dengan reasoning |
| 3 | Creative production | Copy + visual brief 3+ variations |
| 4 | Pre-launch review | Signed-off checklist |
| 5 | Post-launch (24-48h) | Real-time monitoring + automated rules |
| 6 | Iteration (week 2+) | Weekly review, monthly cohort analysis |

## 🛠️ Skills yang Akan Dipakai

- `skills/browser` — automation Ads Manager
- Plus reasoning untuk: targeting strategy, creative direction,
  budget allocation, attribution window decision

## 📝 Catatan Iterasi

- **2026-05-22 v1** — Initial version
- **2026-05-22 v2** — Major rewrite based on 2026 research:
  - Added CAPI/Conversions API requirement (critical post-iOS 14)
  - Added EMQ score targets (minimum 6/10)
  - Added Advantage+ vs Manual decision tree
  - Updated CPL estimates with realistic Indonesia tier-2 numbers
  - Added 6-phase workflow with infrastructure-first approach
  - Added creative testing as primary lever (70% performance)
  - Added attribution window decision (7-day vs 90-day for B2B)
  - Added compliance checklist (Special Ad Category, etc)
  - Added lead response time SLA (<5 min)
