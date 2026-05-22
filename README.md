# 🤖 AI Prompts Library

Kumpulan prompt siap pakai untuk berbagai task — copy, paste, eksekusi.

## 📚 Daftar Prompt

| Kategori | Prompt | Deskripsi |
|---|---|---|
| Marketing | [`iklan-fb-ads`](./iklan-fb-ads/) | Setup Facebook Ads campaign untuk hallowa.id (B2B SaaS) |
| SEO | [`seo-hallowa`](./seo-hallowa/) | Strategi SEO + GEO komprehensif (8 fase) untuk hallowa.id |
| Product | [`feature-gap-analysis`](./feature-gap-analysis/) | Feature gap analysis hallowa.id vs kompetitor + roadmap 12 bulan |
| Product | [`flow-builder-spec`](./flow-builder-spec/) | Technical spec + UX design Visual Flow Builder (chatbot drag-drop) |
| Product | [`marketplace-integration`](./marketplace-integration/) | Integration plan Tokopedia/Shopee/Lazada/TikTok Shop |
| Product | [`mobile-app-plan`](./mobile-app-plan/) | Mobile app dev plan (iOS+Android) untuk agent CS |
| Research | [`customer-interview`](./customer-interview/) | Customer interview script + Mom Test methodology |

> _Akan terus bertambah seiring waktu._

## 🚀 Cara Pakai

1. Buka folder prompt yang dibutuhkan (contoh: [`iklan-fb-ads`](./iklan-fb-ads/))
2. Baca `README.md` di folder itu untuk konteks & cara pakai
3. Copy isi `prompt.txt`:
   - **Cara cepat:** klik file `prompt.txt` → klik tombol **Raw** → `Ctrl+A` → `Ctrl+C`
   - **Atau:** klik tombol **Copy raw file** (icon di kanan atas saat lihat file)
4. Paste ke sesi AI assistant baru sebagai pesan pertama

## 📁 Struktur

```
ai-prompts/
├── README.md                  ← file ini (index)
├── iklan-fb-ads/
│   ├── README.md              ← konteks & instruksi spesifik
│   └── prompt.txt             ← prompt siap copy
└── [kategori-lain]/
    ├── README.md
    └── prompt.txt
```

## 🆕 Konvensi Naming

Tiap prompt baru dibikin sebagai **folder sendiri** di root, dengan nama kebab-case yang deskriptif:

- ✅ `iklan-fb-ads/`
- ✅ `seo-content-writer/`
- ✅ `meta-business-verification/`
- ❌ `prompt1/`, `untitled/`, `IKLAN ADS FB/` (spasi/ambigu)

Tiap folder **wajib** punya:
- `README.md` — konteks bisnis, parameter, mode kerja
- `prompt.txt` — prompt plain text siap copy

Optional:
- `examples/` — screenshot hasil eksekusi
- `variants/` — variasi prompt untuk skenario berbeda

## 📝 Template Prompt Baru

Saat bikin prompt baru, struktur idealnya:

```
═══ KONTEKS ═══
(Bisnis, produk, tujuan)

═══ TUJUAN ═══
(Goal yang spesifik & measurable)

═══ PARAMETER ═══
(Budget, durasi, target, dll)

═══ MODE KERJA ═══
(Step-by-step / auto / interactive)
(Mana yang perlu approval user)

═══ WORKFLOW ═══
(Urutan eksekusi yang diharapkan)

═══ OUTPUT ═══
(Format hasil yang diharapkan)
```

## 🔒 Keamanan

- ❌ Jangan masukin **credential** (token, password, API key) ke prompt apa pun
- ❌ Jangan delegasi keputusan **finansial / legal** ke AI tanpa approval
- ✅ Selalu mode "pandu step-by-step" untuk task yang bisa berdampak (publish, deploy, transfer)
- ✅ User pegang keputusan final di moment kritis

---

_Maintained by [@zesbe](https://github.com/zesbe)_
