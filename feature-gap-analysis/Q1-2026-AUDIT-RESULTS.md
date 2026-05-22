# 📊 Hallowa.id — Feature Gap Analysis Report Q1 2026

> **Tipe:** Executive deliverable (output dari `feature-gap-analysis` prompt)
> **Tanggal:** 2026-05-22
> **Methodology:** Desk research + competitor benchmarking 2026
> **Status:** Initial baseline (perlu di-validate dengan customer interview — lihat [`customer-interview`](../customer-interview/))

---

## 🎯 TL;DR — 5 Hal yang Harus Dilakukan Hallowa Q1 2026

1. **Ship Visual Flow Builder** — kompetitor wajib punya, hallowa belum
2. **Build CRM essentials** (tags, notes, custom fields, unified profile)
3. **Apply ke Tokopedia + Shopee Partner Program SEKARANG** (lead time 4-12 minggu)
4. **Mulai mobile app development** (12-16 minggu, paralel dengan #1 dan #2)
5. **Run customer interview** untuk validate prioritas (4-5 minggu, paralel)

Total investment estimasi Q1 2026: **Rp 1-2 milyar** (3 dev + 1 designer + 1 PM full-time + tools)

---

## 1. Current State — Apa yang Hallowa Punya

### ✅ Strengths

| Aspek | Status | Notes |
|---|---|---|
| Multi-channel (WA/IG/Messenger/Threads) | ✅ Solid | Foundation kuat |
| AI Auto-Reply | ✅ Ada | Tapi keyword-based + AI generic |
| Multi-Agent | ✅ Ada | Assignment + role mgmt |
| Scheduled Posts | ✅ Ada | IG, FB, Threads |
| Analytics | ✅ Ada | Basic, perlu enhanced |
| Security | ✅ Strong | AES-256, 2FA, SOC 2, server ID |
| API Access | ✅ Pro tier+ | Belum tau quality dokumentasi |
| Meta Partner Status | ✅ Official | Trust signal kuat |

### ⚠️ Weaknesses (foundation tapi shallow)

| Aspek | Issue |
|---|---|
| Auto-Reply | Cuma keyword + AI generic, gak ada flow builder |
| Analytics | Basic — kompetitor offer agent perf, CSAT, business KPI |
| Customer Profile | Belum unified across channels |
| API Documentation | Status unknown — dev experience kompetitif? |
| Mobile Experience | Mobile responsive web, **tidak ada native app** |

---

## 2. Gap Analysis vs Kompetitor 2026

### 🔥 CRITICAL GAPS (deal-breaker untuk B2B)

| # | Fitur | hallowa | Qontak | Qiscus | SleekFlow | Wati | Priority |
|---|---|:---:|:---:|:---:|:---:|:---:|:---:|
| 1 | **Visual Flow Builder** | ❌ | ✅ | ✅ | ✅ | ✅ | 🔥 P0 |
| 2 | **Unified Customer Profile** (merge contacts) | ❌ | ✅ | ✅ | ✅ | Partial | 🔥 P0 |
| 3 | **CRM essentials** (tags, notes, custom fields) | ❌ | ✅ Full CRM | ✅ | ✅ | Partial | 🔥 P0 |
| 4 | **Bot-to-Human Handover** (context preserved) | ❌ | ✅ | ✅ | ✅ | ✅ | 🔥 P0 |
| 5 | **Auto-routing** (by topic/team/skill) | ❌ | ✅ | ✅ | ✅ | Partial | 🔥 P0 |
| 6 | **Knowledge Base** for agents | ❌ | ✅ | ✅ | ✅ | ❌ | ⚠️ P1 |
| 7 | **Quick Replies Library** | ❌ | ✅ | ✅ | ✅ | ✅ | ⚠️ P1 |
| 8 | **Working Hours / Out-of-Office** | ❌ | ✅ | ✅ | ✅ | ✅ | ⚠️ P1 |

**Insight:** 5 dari 8 fitur **kompetitor SEMUA punya, hallowa SATU PUN gak punya**. Ini gap yang paling damaging untuk pitch ke B2B prospect.

### ⚠️ IMPORTANT GAPS (kompetitif disadvantage)

| # | Fitur | Notes |
|---|---|---|
| 9 | **Mobile app (iOS + Android)** | Qontak, Qiscus, SleekFlow ada. Hallowa cuma web. |
| 10 | **CSAT/NPS surveys** post-conversation | Standar industri, hallowa belum |
| 11 | **Sentiment analysis AI** | Differentiator AI feature |
| 12 | **Voice notes transcription** | Premium ekspektasi 2026 |
| 13 | **Auto-translate** | Untuk customer asing |
| 14 | **Chat history export** | Compliance enterprise |
| 15 | **Tags & labels** | Prerequisite untuk auto-routing |
| 16 | **Audit logs** lengkap | Compliance enterprise |

### 💡 NICE-TO-HAVE GAPS (differentiator)

| # | Fitur | Differentiation Value |
|---|---|---|
| 17 | **App Marketplace / Extensibility** | Qiscus App Center = moat |
| 18 | **Industry templates** (5 vertikal) | SleekFlow lead, hallowa peluang |
| 19 | **WhatsApp Coexistence** | Hot 2026 |
| 20 | **No-code AI Agent Builder** | Qiscus AgentLabs |
| 21 | **White-label / reseller** | Channel partner play |
| 22 | **Email channel** | Multichannel beyond Meta |
| 23 | **Live chat widget** untuk web | Standar |
| 24 | **SMS channel** | Tier-2 fallback |

### 🇮🇩 INDONESIA-SPECIFIC GAPS (LOCAL MOAT)

| # | Fitur | Why Indonesia-Critical |
|---|---|---|
| 25 | **Tokopedia integration** | UMKM Indonesia dominan di Tokopedia |
| 26 | **Shopee integration** ⚠️ | Bot tidak diizinkan, tapi inbox bisa |
| 27 | **Lazada integration** | Coverage komplit |
| 28 | **TikTok Shop integration** | Fastest growing 2026 |
| 29 | **Local payment** (GoPay, OVO, DANA, ShopeePay, QRIS) | In-chat checkout |
| 30 | **Bahasa Indonesia NLP** (native, bukan AI generic) | Quality auto-reply |
| 31 | **PDP UU compliance** explicit | Trust signal enterprise |
| 32 | **Centang Hijau verification service** | Visibility offering |
| 33 | **Indonesian holiday calendar** auto-OOO | Local UX |
| 34 | **Multi-warehouse / multi-cabang** support | Indonesian SME structure |

**Insight:** Indonesia-specific = **moat sustainable**. Global player (SleekFlow, Trengo) susah copy karena butuh local partnership. Hallowa harus push hard di sini.

---

## 3. Prioritized Roadmap 12 Bulan

### 🔥 Q1 2026 — Close Critical Gaps

**Goal:** Match kompetitor di feature parity essential

| Initiative | Effort | Impact | Quarter Deliverable |
|---|---|---|---|
| Visual Flow Builder MVP | 12 weeks, 3 dev | 🔥 High (deal-breaker) | Ship flow builder dengan 6 node types, 5 templates |
| CRM Essentials (tags, notes, custom fields) | 6 weeks, 2 dev | 🔥 High | Tags, notes, segment, custom fields per contact |
| Unified Customer Profile (merge contacts) | 4 weeks, 1 dev | 🔥 High | Smart matching by phone/email across channels |
| Auto-routing | 3 weeks, 1 dev | 🔥 High | Route by tag, skill, team availability |
| Quick Replies Library | 2 weeks, 1 dev | ⚠️ Medium | Saved replies + variables |
| Working Hours config | 2 weeks, 1 dev | ⚠️ Medium | OOO message, schedule per agent |

**Plus paralel:**
- Customer interview (validate priority)
- Apply Tokopedia/Shopee/Lazada/TikTok Partner Program (lead time 4-12 minggu)

**Q1 Investment:** Rp 800jt – 1.2 milyar (3-4 dev + designer + PM + tools)

### 🚀 Q2 2026 — Indonesia Market Lock-in

**Goal:** Differentiate dengan local moat

| Initiative | Effort | Impact |
|---|---|---|
| Tokopedia integration | 8-10 weeks | 🔥 High |
| Shopee integration (live agent inbox, no bot) | 8-10 weeks | 🔥 High |
| Mobile app (iOS + Android) MVP | 12-16 weeks | 🔥 High |
| WhatsApp Catalog + payment (GoPay/OVO/DANA/QRIS) | 6 weeks | ⚠️ Medium |
| Click-to-WhatsApp Ads (sinergi FB Ads) | 3 weeks | ⚠️ Medium |
| CSAT survey automation | 3 weeks | ⚠️ Medium |
| Bahasa Indonesia NLP fine-tuning | 6 weeks | 💡 Differentiator |

**Q2 Investment:** Rp 1.5 – 2.5 milyar

### 💎 Q3 2026 — Differentiation

**Goal:** Build moat & expand channel

| Initiative | Effort | Impact |
|---|---|---|
| Lazada + TikTok Shop integration | 12 weeks | ⚠️ Medium |
| App Marketplace (3rd party developer onboarding) | 16 weeks | 💡 Long-term moat |
| Industry templates (5 vertikal: e-commerce, edukasi, klinik, real estate, F&B) | 6 weeks | ⚠️ Medium |
| AI Agent Builder no-code | 8 weeks | 💡 Differentiator |
| Knowledge Base for agents | 4 weeks | ⚠️ Medium |
| Sentiment analysis | 3 weeks | 💡 Premium feature |

**Q3 Investment:** Rp 1.2 – 2 milyar

### 🏗️ Q4 2026 — Polish & Scale

| Initiative | Notes |
|---|---|
| Email channel | Beyond Meta = multichannel hub |
| SMS channel | Indonesia tier-2 |
| Live chat widget | Standar |
| White-label option | Reseller channel |
| Enterprise features (SSO, audit logs, advanced compliance) | Untuk Enterprise tier |
| Advanced analytics (cohort, retention, customer journey) | Data insights |
| WhatsApp Coexistence | Hot 2026 |

---

## 4. Pricing Tier Re-design Recommendation

### Current Tier vs Recommended

| Tier | Current | Issue | Recommended |
|---|---|---|---|
| Free | Rp 0, 100 kontak, 1 user | Cuma untuk eksplorasi, OK | Tetap |
| Starter | Rp 199k, 1k kontak, 3 user | Terlalu sempit dengan fitur baru | **Naik ke Rp 299k**, 2.5k kontak, 3 user, +flow builder basic |
| **Growth (NEW)** | — | Gap antara Starter & Pro terlalu jauh | **Rp 499k**, 5k kontak, 5 user, +CRM essentials, +1 marketplace |
| Pro | Rp 599k, 10k kontak, 10 user | Pro terlalu mahal jump dari Starter (3x) | **Rp 999k**, 15k kontak, 10 user, +all marketplace, +mobile app, +flow builder advanced |
| Enterprise | Custom | OK | Tetap |

### Add-ons (per-use pricing)

- **Tokopedia integration**: +Rp 99k/bulan (di Pro+)
- **Shopee integration**: +Rp 99k/bulan
- **Mobile app**: include di Pro+
- **AI Agent Builder**: +Rp 199k/bulan (Pro+)
- **WhatsApp message volume** beyond quota: per-message metered

---

## 5. Competitive Positioning Statement

### Sweet Spot Hallowa (after Q1 2026 ships)

> **"For Indonesian SMEs running customer service across WhatsApp, Instagram, Messenger, AND marketplaces (Tokopedia/Shopee), HalloWa is the only platform that combines unified inbox, AI auto-reply, and full Indonesia marketplace integration with server in Indonesia and PDP-compliant security."**

### vs Mekari Qontak
- Qontak lebih lengkap di **CRM features** dan **enterprise process**
- Hallowa unggul di: **harga lebih terjangkau** untuk UMKM, **simpler onboarding**, **Meta-first stack** lebih dalam
- Target customer: UMKM yang Qontak terlalu kompleks

### vs Qiscus
- Qiscus lebih dalam di **enterprise features** dan **ekosistem channel** (20+)
- Hallowa unggul di: **focus B2C messaging via Meta+marketplace**, **harga lebih SME-friendly**
- Target customer: SMB e-commerce yang mainly butuh Meta + marketplace

### vs Wati
- Wati cuma fokus WhatsApp
- Hallowa unggul di: **multi-channel** dari awal, **Indonesia-specific**
- Target customer: bisnis yang butuh beyond WhatsApp

---

## 6. Risk Register

| # | Risk | Likelihood | Impact | Mitigation |
|---|---|:---:|:---:|---|
| 1 | Visual Flow Builder MVP molor >12 minggu | High | High | Hire agency burst, atau scope down |
| 2 | Tokopedia/Shopee partnership ditolak / lambat | Medium | High | Apply ke beberapa marketplace paralel, plus aggregator fallback |
| 3 | Mobile app delivery telat | Medium | Medium | Outsource ke agency Indonesia (Eyro, Ekipa, dll) |
| 4 | Customer churn ke Qontak/Qiscus saat menunggu fitur | Medium | High | Communicate roadmap explicit, beta program early access |
| 5 | Pricing change resistance | Medium | Medium | Grandfather existing customer, gradual rollout |
| 6 | Big Tech (Meta direct B2B) enter market | Low | Critical | Build Indonesia-specific moat (marketplace, payment) |
| 7 | Talent shortage (mobile dev, flow builder UX) | High | Medium | Remote hire, agency partnership |
| 8 | Capital intensity terlalu besar (Rp 4-8 milyar/tahun) | Medium | High | Phase rollout, validate before build |

---

## 7. Top 10 Must-Ship Dalam 6 Bulan

Sorted by priority:

1. **Visual Flow Builder** (Q1)
2. **CRM essentials** (Q1)
3. **Unified Customer Profile** (Q1)
4. **Auto-routing** (Q1)
5. **Tokopedia integration** (Q2)
6. **Shopee integration** (Q2)
7. **Mobile app MVP** (Q2)
8. **Quick Replies + Working Hours** (Q1)
9. **Bot-to-human handover proper** (Q1)
10. **CSAT survey automation** (Q2)

---

## 8. What NOT To Build (Yet)

Anti-recommendations:

- ❌ **White-label** sebelum 50+ enterprise customer (overengineering)
- ❌ **App Marketplace** sebelum 10+ third-party developer interested
- ❌ **Voice/video calling** (Meta sendiri belum push hard di WA Business)
- ❌ **Email channel** sebelum core messaging excellent (focus first)
- ❌ **AI Agent Builder** sebelum Visual Flow Builder shipped
- ❌ **Lazada + TikTok Shop** sebelum Tokopedia + Shopee proven
- ❌ **Custom integration per-customer** (cuma Enterprise tier dengan minimum commit)

---

## 9. Validation Plan (Critical Next Step)

**Sebelum invest Rp 4-8 milyar/tahun**, validate dulu via customer interview:

1. Run [`customer-interview`](../customer-interview/) prompt
2. Recruit 30+ interviewee (10 existing customer, 10 lost lead, 10 prospect)
3. Validate top 10 must-ship list
4. Update prioritization based on insights
5. Re-baseline this report di Q2 (kuartalan refresh)

**Deadline validation: 4-5 minggu (target completion: end June 2026)**

---

## 10. Methodology Notes

**Sources:**
- Hallowa.id site fetch (May 2026)
- Mekari Qontak features pages
- Qiscus blog & feature documentation
- SleekFlow product overview
- ChakraHQ "15 Important WhatsApp API Features 2026"
- AiSensy "Top 14 WhatsApp Automation Tools 2026"
- WhatsApp Business Platform official docs
- Yellow.ai docs (Tokopedia & Shopee channel)
- Industry reports: tripledart.com, saashero.net (B2B SaaS benchmarks)

**Limitations:**
- Belum direct interview hallowa customer (asumsi internal — VALIDATE)
- Belum sign-up trial kompetitor (UX comparison superficial)
- Belum analisis pricing kompetitor secara detail
- Belum hitung TAM/SAM Indonesia messaging SaaS market

**Next research phase (recommended):**
- Sign up free trial Qontak, Qiscus, SleekFlow, Wati
- Document UX flows kunci
- Interview 5-10 hallowa customer untuk validate
- Cek G2/Capterra reviews kompetitor untuk customer pain
- Pricing tier deep-dive

---

_Generated: 2026-05-22_
_Next review: 2026-08-22 (quarterly)_
_Owner: Product team hallowa.id_
