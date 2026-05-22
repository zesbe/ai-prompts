# FB Ads Setup Prompt — hallowa.id

Copy seluruh blok di bawah ini, paste ke sesi AI assistant baru sebagai pesan pertama.

---

```
Tolong bantu setup Facebook Ads campaign untuk hallowa.id.

═══ KONTEKS BISNIS ═══
hallowa.id adalah SaaS unified messaging platform B2B di Indonesia.
- Produk: integrasi WhatsApp Business API, Instagram, Messenger, Threads
  dalam satu dashboard
- Status: Official Meta Business Partner
- USP utama: Unified inbox, AI auto-reply, multi-agent, server Indonesia,
  enterprise security (AES-256, 2FA, SOC 2)
- Target customer: UMKM sampai enterprise yang handle customer service
  multi-channel
- Model bisnis: Freemium → Starter Rp199k/bln → Pro Rp599k/bln →
  Enterprise custom
- Free trial: 14 hari semua paket berbayar
- Landing page utama: https://app.hallowa.id/register

═══ TUJUAN CAMPAIGN ═══
Primary objective: Lead Generation / Trial Signup
Goal: orang daftar di app.hallowa.id/register dan mulai trial 14 hari.
Saranin objective FB Ads yang paling tepat (Conversions vs Leads vs
Traffic) berdasarkan status pixel & best practice B2B SaaS.

═══ BUDGET ═══
- Budget harian: Rp 100.000/hari
- Durasi: 30 hari
- Total budget cap: Rp 3.000.000
- Strategi alokasi: saranin lo — apakah split testing dulu 7-10 hari lalu
  scale yang menang, atau langsung evergreen dari awal. Tunggu approval
  gue sebelum eksekusi.

═══ TARGET AUDIENCE ═══
Tolong saranin targeting yang masuk akal untuk B2B SaaS messaging di
Indonesia. Pertimbangkan:
- Lokasi (Indonesia all atau tier-1 cities dulu: Jakarta, Surabaya,
  Bandung, Medan?)
- Job title / interest (founder UMKM, owner online shop, CS manager,
  marketing manager, e-commerce, dll)
- Behavior (engaged shoppers, small business owners, sudah pakai
  WhatsApp Business)
- Lookalike audience kalau pixel data udah cukup
- Saranin minimal 2-3 ad set dengan audience berbeda untuk testing

═══ CREATIVE ═══
Belum ada creative siap pakai. Tolong:
1. Saranin format paling efektif untuk B2B SaaS Indonesia (single image
   / carousel / video / reels)
2. Draftin minimal 3 variasi copy ad lengkap:
   - Headline (max 40 karakter)
   - Primary text (max 125 karakter ideal)
   - Description
   - CTA button (Sign Up / Learn More / Try for Free / dll)
3. Saranin angle visual:
   - Screenshot dashboard?
   - Testimoni customer (Diana Putri, Andi Wijaya, Sarah Nurul ada di
     site)?
   - Pain point ("CS lo masih buka 4 app berbeda?")
   - Hasil ("Response time turun dari 2 jam ke 5 menit")
4. Setelah lo kasih draft, gue yang siapin asetnya. Lo pandu spec
   ukuran, format, dll.

═══ TECHNICAL ═══
- FB Pixel: belum tau status, tolong cek di hallowa.id apakah udah
  terpasang. Cek lewat browser (View Page Source) atau curl. Kalau
  belum ada, kasih tau cara pasangnya.
- Akun FB & Business Manager: udah login di Chrome
- Payment method di Ads Manager: gue cek sendiri sebelum publish

═══ MODE KERJA ═══
PANDU STEP-BY-STEP. Pakai skills/browser dengan profile Chrome gue
(node ~/.claude/skills/browser/start.js --profile).

Aturan:
- Tiap halaman penting: screenshot + jelasin opsinya dengan jelas
- Tunggu approval gue sebelum lanjut step berikutnya
- JANGAN auto-publish — di tahap akhir, lo BERHENTI dan biar GUE yang
  klik "Publish Campaign"
- Kalau ada keputusan strategis (target detail, bidding strategy,
  optimization event, attribution window), tanya gue dulu jangan
  asumsi
- Kalau lo nemu ada yang janggal di Ads Manager (peringatan, error,
  policy issue), berhenti dan lapor

═══ WORKFLOW URUTAN ═══
1. Cek status FB Pixel di hallowa.id (browser/curl ke source code)
2. Buka Ads Manager via skills/browser (dengan profile)
3. Screenshot tampilan awal Ads Manager + kasih tau Ad Account ID
   yang aktif
4. Saranin struktur campaign: berapa ad set, berapa ad per ad set,
   audience masing-masing
5. Tunggu approval gue → lalu buat Campaign
6. Pandu setup ad set satu per satu (audience, placement, budget,
   schedule, optimization)
7. Pandu setup ad creative (upload image, isi copy, preview)
8. Sebelum publish: full review semua setting, tunggu approval gue
9. Gue yang klik "Publish"
10. Setelah live: kasih checklist hal yang harus gue monitor di
    24-48 jam pertama

═══ OUTPUT YANG GUE HARAPKAN ═══
- Setiap step: screenshot + penjelasan singkat
- Setiap keputusan strategis: opsi-opsi + rekomendasi lo + alasannya
- Akhir sesi: ringkasan apa yang udah di-setup + monitoring plan
```
