# Meta Pixel + CAPI Setup Guide — hallowa.id

> **Untuk:** Dev team hallowa.id
> **Status sekarang:** Pixel "HalloWa Pixel" baru dibuat di **Business Manager HalloWa** (1522280809047027). Pixel ID baru harus dicek di Events Manager. Pixel script belum terpasang di hallowa.id, CAPI belum setup, 0 events flowing.
> **Estimasi waktu:** 2-4 jam dev (pixel) + 4-8 jam dev (CAPI proper) = **1-2 hari kerja total**.
> **Generated:** 2026-05-22 (post-audit Phase 1 FB Ads campaign)

## ⚠️ UPDATE 2026-05-22 (sesi 2):

- **Pixel LAMA `1382447226543529`** ("HalloWa") = di **personal account Yudi Haryanto**, bukan di Business HalloWa. **JANGAN PAKAI ini.**
- **Pixel BARU "HalloWa Pixel"** = baru dibuat di Business HalloWa (1522280809047027). ID-nya: **[CEK_DI_EVENTS_MANAGER]** — perlu diganti di kode script di bawah sebelum implement.
- **Ad Account BARU "Hallowa"** = `1950462445655335` (di Business HalloWa, currency IDR, timezone Asia/Jakarta).
- Semua referensi ke pixel ID `1382447226543529` di guide ini harus **diganti** ke pixel ID baru sebelum dev pasang.

---

## 🎯 TL;DR — yang harus dilakukan

1. ✅ **Pasang pixel script** di `<head>` semua page hallowa.id + app.hallowa.id
2. ✅ **Tambah event tracking** di app.hallowa.id (PageView, ViewContent, CompleteRegistration, StartTrial, Subscribe)
3. ✅ **Setup CAPI** (Conversions API) — pilih satu: CAPI Gateway / Stape / custom
4. ✅ **Test events** di Events Manager → Test Events tab
5. ✅ **Verify EMQ score** minimum 6/10 (target 8+)
6. ✅ **Wait 24-48 jam** untuk algoritma FB siap → baru launch campaign

---

## 1. Pixel Browser-Side Implementation

### File: Tambahkan di `<head>` semua HTML page

**Untuk hallowa.id (SvelteKit, lihat di [layout root]):**

```svelte
<svelte:head>
  <!-- Meta Pixel Code -->
  <script>
    !function(f,b,e,v,n,t,s)
    {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
    n.callMethod.apply(n,arguments):n.queue.push(arguments)};
    if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
    n.queue=[];t=b.createElement(e);t.async=!0;
    t.src=v;s=b.getElementsByTagName(e)[0];
    s.parentNode.insertBefore(t,s)}(window, document,'script',
    'https://connect.facebook.net/en_US/fbevents.js');
    fbq('init', 'PIXEL_ID_BARU_DARI_BUSINESS_MANAGER'); // ⚠️ Ganti ke pixel HalloWa Pixel ID yg baru
    fbq('track', 'PageView');
  </script>
  <noscript>
    <img height="1" width="1" style="display:none"
      src="https://www.facebook.com/tr?id=PIXEL_ID_BARU&ev=PageView&noscript=1" />
  </noscript>
  <!-- End Meta Pixel Code -->
</svelte:head>
```

**Verifikasi:**
- Buka hallowa.id di Chrome → Network tab → filter "facebook"
- Harus ada request ke `https://www.facebook.com/tr/?id=PIXEL_ID_BARU&ev=PageView...`
- Atau install [Meta Pixel Helper Chrome Extension](https://chrome.google.com/webstore/detail/meta-pixel-helper) → buka site → harus muncul ✅

---

## 2. Custom Events di app.hallowa.id

Tracking events yang krusial untuk B2B SaaS lead funnel:

### Event taxonomy

| Event | Dipasang di | Trigger | Data |
|---|---|---|---|
| `PageView` | Semua page | Auto | URL, referrer |
| `ViewContent` | /pricing | Page view pricing | content_name, content_category |
| `Lead` | Form contact / sales inquiry | Form submit | value, currency |
| `CompleteRegistration` | /register | Setelah signup sukses | value, currency, content_name (plan) |
| `StartTrial` | Trial activation | Setelah verify email + activate | value, currency, plan |
| `Subscribe` | Upgrade ke paid | Payment sukses | value (tier price), currency, predicted_ltv |
| `Purchase` | Optional, sama dengan Subscribe untuk SaaS | — | — |

### Code examples

**ViewContent (pricing page):**
```javascript
// /pricing page - on mount
if (typeof fbq !== 'undefined') {
  fbq('track', 'ViewContent', {
    content_name: 'Pricing Page',
    content_category: 'pricing',
    content_type: 'product_group'
  });
}
```

**CompleteRegistration (after signup):**
```javascript
// On successful registration
if (typeof fbq !== 'undefined') {
  fbq('track', 'CompleteRegistration', {
    content_name: selectedPlan, // 'starter' | 'pro' | 'enterprise'
    status: 'free_trial',
    currency: 'IDR',
    value: 0 // free trial = 0 value initially
  });
}
```

**StartTrial:**
```javascript
// After user activates trial (e.g., adds first contact, sends first message)
if (typeof fbq !== 'undefined') {
  fbq('track', 'StartTrial', {
    content_name: planName,
    currency: 'IDR',
    value: planMonthlyPrice, // 199000 / 599000
    predicted_ltv: planMonthlyPrice * 12 // estimasi LTV 12 bulan
  });
}
```

**Subscribe (paid conversion):**
```javascript
// On successful payment (after webhook from payment gateway)
if (typeof fbq !== 'undefined') {
  fbq('track', 'Subscribe', {
    content_name: planName,
    currency: 'IDR',
    value: amountPaid, // actual amount
    predicted_ltv: amountPaid * 12,
    order_id: orderId
  });
}
```

### Best practice

1. **Wrap all `fbq()` calls dengan `typeof fbq !== 'undefined'`** — biar gak crash kalau pixel blocked (ad-blocker, slow load)
2. **Add `event_id` untuk deduplication** dengan CAPI events:
   ```javascript
   const eventId = crypto.randomUUID();
   fbq('track', 'CompleteRegistration', {...}, {eventID: eventId});
   // Send same eventId via CAPI server-side
   ```
3. **Test di Events Manager → Test Events tab** sebelum deploy ke prod

---

## 3. CAPI (Conversions API) Setup

⚠️ **CRITICAL 2026:** Pixel-only setup miss **50%+ conversion** post-iOS 14. CAPI **WAJIB** untuk akurasi.

### Pilih salah satu approach (urut dari paling gampang ke paling proper):

#### Option A — CAPI Gateway (Meta-managed, no-code) ⭐ RECOMMENDED untuk start

Meta hosts a server yang receive event browser-side dan forward server-side ke CAPI.

**Setup:**
1. Buka [Events Manager](https://business.facebook.com/events_manager/) → Pixel "HalloWa Pixel" (ID baru, cek di Events Manager)
2. Klik **Settings** tab
3. Scroll ke **Conversions API Gateway** section
4. Klik **Set up Conversions API Gateway**
5. Pilih cloud provider (AWS / GCP / Azure / DigitalOcean)
6. Run deploy script (Meta provides terraform/cloud formation)
7. Configure subdomain: `events.hallowa.id` → CAPI Gateway endpoint
8. Verify

**Pros:** No custom code, Meta-managed
**Cons:** Less control, vendor-locked

#### Option B — Partner Integration (Stape, Segment) ⭐ RECOMMENDED untuk fleksibilitas

Pakai 3rd party data layer yang handle CAPI.

**Stape (paling populer untuk SvelteKit/SaaS):**
1. Sign up [stape.io](https://stape.io)
2. Create container, deploy ke domain (free tier ada)
3. Install **GTM server-side** + **Facebook Conversions API tag**
4. Configure events mapping browser → server
5. Test di Stape preview mode + Events Manager Test Events

**Cost:** $20-100/month tergantung volume

#### Option C — Custom Server-Side Implementation (most control)

Tulis sendiri di backend hallowa.

**Sample Node.js implementation:**

```javascript
// File: src/lib/server/meta-capi.ts
import crypto from 'crypto';

const PIXEL_ID = process.env.META_PIXEL_ID; // Pixel HalloWa Pixel ID baru, set di env vars
const ACCESS_TOKEN = process.env.META_CAPI_ACCESS_TOKEN; // get from Events Manager → Settings → API Access Token
const TEST_EVENT_CODE = process.env.META_CAPI_TEST_CODE; // optional, for testing

function hash(value: string): string {
  if (!value) return '';
  return crypto.createHash('sha256').update(value.trim().toLowerCase()).digest('hex');
}

interface CapiEvent {
  event_name: string;
  event_time: number;
  event_id: string; // for dedup with browser pixel
  event_source_url?: string;
  user_data: {
    em?: string[];      // email hashed
    ph?: string[];      // phone hashed
    fbc?: string;       // from _fbc cookie
    fbp?: string;       // from _fbp cookie
    client_ip_address?: string;
    client_user_agent?: string;
    external_id?: string[]; // user ID hashed
  };
  custom_data?: {
    currency?: string;
    value?: number;
    content_name?: string;
    content_category?: string;
  };
  action_source: 'website';
}

export async function sendCapiEvent(event: CapiEvent) {
  const url = `https://graph.facebook.com/v21.0/${PIXEL_ID}/events`;
  
  const body: any = {
    data: [event],
    access_token: ACCESS_TOKEN
  };
  
  if (TEST_EVENT_CODE) {
    body.test_event_code = TEST_EVENT_CODE;
  }
  
  try {
    const res = await fetch(url, {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(body)
    });
    const result = await res.json();
    
    if (result.error) {
      console.error('[CAPI] Error:', result.error);
    } else {
      console.log('[CAPI] Success:', result.events_received);
    }
    return result;
  } catch (err) {
    console.error('[CAPI] Network error:', err);
  }
}

// Helper untuk extract user data dari request
export function extractUserData(request: Request, user?: { email?: string; phone?: string; id?: string }) {
  const cookies = request.headers.get('cookie') || '';
  const fbc = cookies.match(/_fbc=([^;]+)/)?.[1];
  const fbp = cookies.match(/_fbp=([^;]+)/)?.[1];
  
  return {
    em: user?.email ? [hash(user.email)] : undefined,
    ph: user?.phone ? [hash(user.phone)] : undefined,
    external_id: user?.id ? [hash(user.id)] : undefined,
    fbc,
    fbp,
    client_ip_address: request.headers.get('x-forwarded-for') || request.headers.get('x-real-ip') || undefined,
    client_user_agent: request.headers.get('user-agent') || undefined
  };
}
```

**Usage di SvelteKit endpoint:**

```typescript
// src/routes/api/auth/register/+server.ts
import { sendCapiEvent, extractUserData } from '$lib/server/meta-capi';

export async function POST({ request }) {
  const body = await request.json();
  
  // 1. Process registration (your existing code)
  const user = await createUser(body);
  
  // 2. Send CAPI event
  const eventId = body.event_id || crypto.randomUUID(); // browser pixel passes same event_id
  
  await sendCapiEvent({
    event_name: 'CompleteRegistration',
    event_time: Math.floor(Date.now() / 1000),
    event_id: eventId,
    event_source_url: request.headers.get('referer') || 'https://app.hallowa.id/register',
    user_data: extractUserData(request, user),
    custom_data: {
      content_name: body.plan,
      currency: 'IDR',
      value: 0
    },
    action_source: 'website'
  });
  
  return new Response(JSON.stringify({ ok: true, user }), {
    headers: { 'Content-Type': 'application/json' }
  });
}
```

### Generate CAPI Access Token

1. Events Manager → Pixel HalloWa → Settings tab
2. Section "Conversions API" → klik **Generate access token**
3. Copy token → simpan di env var `META_CAPI_ACCESS_TOKEN` (production secrets)
4. **Jangan commit ke git** ⚠️

---

## 4. Event Deduplication (Browser + Server)

Tanpa dedup, conversion bakal di-double-count (browser + server kirim event sama). FB perlu `event_id` yang sama di browser pixel + CAPI.

**Browser side:**
```javascript
const eventId = crypto.randomUUID();
fbq('track', 'CompleteRegistration', { ... }, { eventID: eventId });

// Send eventId ke server via fetch / form
fetch('/api/auth/register', {
  method: 'POST',
  body: JSON.stringify({ ...formData, event_id: eventId })
});
```

**Server side:** pakai `event_id` yang sama dari request.

---

## 5. EMQ Score Optimization (target ≥6/10, ideal 8+)

EMQ (Event Match Quality) tergantung user data yang dikirim. Lebih banyak data = lebih bagus matching.

| Data | Wajib | EMQ Impact |
|---|---|---|
| `em` (email hashed SHA-256) | ✅ Yes | High |
| `ph` (phone hashed) | ✅ Yes | High |
| `external_id` (user ID hashed) | ✅ Yes | High |
| `fbc` (from `_fbc` cookie) | Highly recommended | High |
| `fbp` (from `_fbp` cookie) | Highly recommended | Medium |
| `client_ip_address` | Highly recommended | Medium |
| `client_user_agent` | Highly recommended | Medium |
| `fn`, `ln` (first/last name hashed) | Optional | Low |
| `ct`, `st`, `zp`, `country` (location hashed) | Optional | Low |

**Best practice:**
- Hash dengan SHA-256 (lowercase, trimmed)
- Send ALL available user data — FB filter sendiri yang relevan
- Test di Events Manager → Diagnostics tab → cek EMQ score per event

---

## 6. Aggregated Event Measurement (AEM) — Domain Verification

iOS 14+ requires AEM setup untuk attribution work properly.

### Steps:

1. **Verify domain `hallowa.id`**:
   - Business Settings → Brand Safety → Domains
   - Add `hallowa.id`
   - Verify via DNS TXT record:
     ```
     facebook-domain-verification=XXXXXXXXX
     ```
   - Atau via meta tag di `<head>`:
     ```html
     <meta name="facebook-domain-verification" content="XXXXXXXXX" />
     ```
   - Atau via HTML file upload

2. **Configure 8 prioritized events** di Events Manager:
   - Events Manager → Aggregated Event Measurement
   - Pilih hallowa.id domain
   - Drag-drop 8 events (urutan = priority):
     1. **Subscribe** (paid conversion — highest value)
     2. **StartTrial**
     3. **CompleteRegistration**
     4. **Lead**
     5. **ViewContent** (pricing)
     6. **AddToCart** (kalau ada — proxy event)
     7. **InitiateCheckout** (kalau ada)
     8. **PageView**
   - Save

---

## 7. Test Events Sebelum Live

### Test plan:

1. **Browser test:**
   - Install [Meta Pixel Helper](https://chrome.google.com/webstore/detail/meta-pixel-helper) Chrome extension
   - Buka hallowa.id → harus muncul ✅ "1 pixel found, fired event: PageView"
   - Buka /pricing → harus fire ViewContent
   - Daftar account baru → harus fire CompleteRegistration

2. **CAPI test:**
   - Events Manager → Test Events tab
   - Copy Test Event Code (format: `TEST12345`)
   - Set ENV `META_CAPI_TEST_CODE=TEST12345`
   - Trigger event di staging → harus muncul real-time di Test Events

3. **Dedup test:**
   - Verify `event_id` sama antara browser & server event
   - Events Manager → Diagnostics → "Duplicate events" check should show low number

### Expected output (after 24 jam):

- Events Manager → Overview: chart events naik (PageView paling banyak)
- EMQ Score per event: target 6+ (warning kalau < 5)
- Settings → Conversions API health: status "Active"
- Diagnostics tab: minimal warning

---

## 8. Privacy & Consent (PDP UU 27/2022 Compliance)

⚠️ Indonesia PDP UU butuh **explicit consent** untuk tracking. Pasang cookie consent banner:

**Implementasi minimal:**
```html
<!-- Banner -->
<div id="cookie-consent" style="position:fixed; bottom:0; ...">
  <p>HalloWa pakai cookies untuk improve experience & marketing.</p>
  <button onclick="acceptCookies()">Terima</button>
  <button onclick="rejectCookies()">Tolak</button>
</div>

<script>
  function acceptCookies() {
    localStorage.setItem('cookie_consent', 'accepted');
    // Initialize pixel
    fbq('consent', 'grant');
    document.getElementById('cookie-consent').style.display = 'none';
  }
  function rejectCookies() {
    localStorage.setItem('cookie_consent', 'rejected');
    fbq('consent', 'revoke');
    document.getElementById('cookie-consent').style.display = 'none';
  }
  // On load, check consent
  if (localStorage.getItem('cookie_consent') === 'rejected') {
    fbq('consent', 'revoke');
  }
</script>
```

**Recommended library:** [Klaro!](https://klaro.org) atau [Cookiebot](https://cookiebot.com) — proper consent management.

---

## 9. Rollout Checklist

### Pre-deployment
- [ ] Pixel script di staging environment, test dengan Pixel Helper
- [ ] CompleteRegistration / StartTrial / Subscribe events test
- [ ] CAPI access token generated, stored di env vars
- [ ] CAPI test events fire correctly (Events Manager Test Events tab)
- [ ] Domain hallowa.id verified
- [ ] 8 prioritized AEM events configured
- [ ] Cookie consent banner active
- [ ] PDP UU compliance review (legal)

### Production deployment
- [ ] Deploy pixel script to hallowa.id (homepage, pricing, blog, all pages)
- [ ] Deploy custom events to app.hallowa.id (register, trial, subscribe)
- [ ] Deploy CAPI server-side integration
- [ ] Remove TEST_EVENT_CODE from production env
- [ ] Monitor Events Manager for first 4 jam — events should flow

### Post-deployment monitoring (first 7 days)
- [ ] Daily check Events Manager Overview
- [ ] EMQ score per event ≥ 6/10
- [ ] CAPI health: Active, no errors
- [ ] Pixel Helper green check di hallowa.id + app.hallowa.id
- [ ] Dedup rate (browser vs server) close to 100%
- [ ] No critical issues in Diagnostics tab

### Ready for FB Ads campaign launch
- [ ] Minimum 24-48 jam events flowing
- [ ] Custom audience "Visitor 30 days" sudah ada user (cek di Audiences)
- [ ] CompleteRegistration event di-fire minimal 5-10x dari real test users
- [ ] **Resume FB Ads campaign yang udah di-draft (Tinjau dan Terbitkan)**

---

## 10. Estimasi Effort & Timeline

| Task | Effort | Owner |
|---|---|---|
| Pixel browser-side install | 2-4 jam | Frontend dev |
| Custom events di app.hallowa.id | 4-8 jam | Frontend + backend dev |
| CAPI implementation (Option A: Gateway) | 2-4 jam | DevOps |
| CAPI implementation (Option B: Stape) | 4-6 jam | Frontend dev |
| CAPI implementation (Option C: Custom) | 8-16 jam | Backend dev |
| Domain verification | 30 menit | DevOps |
| AEM event setup | 30 menit | Marketing/PM |
| Cookie consent | 2-4 jam | Frontend dev |
| Testing & QA | 4-8 jam | QA |
| **TOTAL (Option A path)** | **1.5-2 hari** | Mixed |
| **TOTAL (Option C path)** | **3-4 hari** | Mixed |

Recommended path untuk hallowa: **Option A (CAPI Gateway)** untuk MVP cepat, migrate ke Option C dalam 1-3 bulan kalau butuh more control.

---

## 📚 References

- [Meta Pixel Documentation](https://developers.facebook.com/docs/meta-pixel)
- [Conversions API Documentation](https://developers.facebook.com/docs/marketing-api/conversions-api/)
- [Conversions API Gateway](https://www.facebook.com/business/help/2916157348606567)
- [Aggregated Event Measurement](https://www.facebook.com/business/help/721422165168355)
- [iOS 14+ Implementation Guide](https://www.facebook.com/business/help/331612538028890)
- [Stape (CAPI Partner)](https://stape.io)

---

_Generated: 2026-05-22_
_Owner: Dev team hallowa.id_
_Linked to: [iklan-fb-ads](../README.md) prompt v2_
