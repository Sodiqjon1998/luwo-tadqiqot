# 08 — Jonli dars: bevosita kuzatuv

> 2026-09-25 da haqiqiy 6-sinf darsi (16 o'quvchi) davomida o'qituvchi
> panelidan kuzatildi. Darsni o'qituvchi o'zi o'tkazdi, kuzatuvchi faqat
> sahifa holati, DOM va tarmoq so'rovlarini o'qidi — hech narsa bosilmadi.
> Bolalar ismlari, PIN kodlar, dars kodi va maktab nomi yozilmagan.

---

## Vaqt chizig'i

| Vaqt | Hodisa |
|---|---|
| 09:11 | Sessiya yaratildi — lobby ochildi |
| 09:19–09:20 | Bolalar kirdi (16 dan 12 tasi) |
| 09:20:27 | "Darsni boshlash" → **Taqdimot** (16 slayd) |
| 09:28 | Oxirgi slayd — "Topshiriqlarni ochish" yoqildi |
| 09:29 | **Amaliyot** (11 topshiriq) |
| 09:43 | Birinchi bola barcha topshiriqlarni tugatdi |
| 09:44 | **O'yin maydoni** (bir necha soniya) → **Viktorina** (8 savol) |
| 09:48 | Viktorina g'oliblari (podium) |
| 09:48:59 | O'qituvchi paneldan **majburan chiqarildi** — pastda §8 |

Taqdimot ~9 daq · amaliyot ~15 daq · viktorina ~4,5 daq. Jami ~28 daqiqa.

---

## 1. Dars tuzilishi — 3 emas, 4 qadam

Monitor sarlavhasida `DARS · 4 QADAMDAN N-SI` yozuvi va 4 ta chip turadi:

```
1. Taqdimot       slaydlar + o'qituvchi izohlari
2. Amaliyot       "Topshiriqlar"                 lucide-list-checks
3. O'yin maydoni  "O'yin maydoni"                lucide-gamepad-2
4. Viktorina      "{mavzu} — o'zingni tekshir"   lucide-target
```

**O'yin maydoni** oldingi hujjatlarda umuman yo'q edi. Tugagan qadam
chipi yashil ✓ bilan belgilanadi. Chip ustiga kursor olib borilsa, popover
ochiladi ("Slayd tanlash uchun blok ustiga kursorni olib boring").

Qadamlar orasidagi o'tish **faqat o'qituvchi qo'lida**:

| Qayerdan | Tugma | Shart |
|---|---|---|
| Lobby → Taqdimot | "Darsni boshlash" | Kamida 1 bola ulangan + tasdiqlash dialogi |
| Taqdimot → Amaliyot | "Topshiriqlarni ochish →" | **Faqat oxirgi slaydda** yoqiladi |
| Amaliyot → keyingi | "Davom etish →" | Hamma tugatishi shart emas |
| → Viktorina | "Viktorinani boshlash" | |
| Viktorina → yakun | "Viktorina yakuni" | Oxirgi savoldan keyin |

---

## 2. Lobby

Marshrut: `/monitor` (lobby ham, monitor ham shu yerda).

- Sarlavha: `{sinf} · {dars nomi}`
- Katta **6 xonali kod** — Geist Mono, 56px, bold, `tracking-[0.14em]`,
  `tabular-nums`
- Ikki guruh: **HALI KIRMADI · N** (tepada) va **SINFDA · N** (pastda,
  ism oldida ✓)
- Har bir bola — raqam, avatar va to'liq F.I.Sh. yozilgan `<button>` kartochka
- Pastki panel: `Ulandi: 16 tadan N tasi` · **Sessiyani bekor qilish** ·
  **Darsni boshlash** (0 ulanganda o'chirilgan)

**"SINFDA" va "Ulandi" — har xil sonlar.** Bir paytda `SINFDA · 11`, lekin
`Ulandi: 16 tadan 10 tasi` ko'rindi. Ya'ni SINFDA — sessiyaga qo'shilganlar,
Ulandi — ayni damda onlayn bo'lganlar.

Boshlash dialogi:

> *"{sinf} uchun {dars}ni boshlaysizmi? 16 o'quvchidan 12 nafari ichkarida —
> kechikkanlar dars davomida ham qo'shilishi mumkin."* — [Hali emas] [Boshlash]

Dars davomida ham qo'shilish kodi sarlavhada turadi (nusxa olish tugmasi
bilan) — kechikkanlar uchun.

---

## 3. Taqdimot rejimi

```
● TAQDIM ETILMOQDA
{sinf} · {dars}              [Qo'shilish kodi ______ ⧉]  [Darsni yakunlash ⌄]
DARS · 4 QADAMDAN 1-SI   [chiplar]
┌──────────────────────────────┬──────────────────────────┐
│ Slayd 1 / 16                 │ O'QITUVCHI UCHUN IZOHLAR │
│   (slayd)                    │  MAQSAD                  │
│                              │  NIMA DEYISH KERAK       │
│ ‹ [miniatyuralar lentasi] ›  │  SINFDAN SO'RANG         │
│                              │  JAVOB                   │
└──────────────────────────────┴──────────────────────────┘
[O'quvchilar PIN kodi ⌄]   [✋ Diqqat]   [Topshiriqlarni ochish →]
```

- **Slaydni o'qituvchi suradi** — miniatyuralar yoki strelkalar bilan.
  Slaydlar ~30–60 soniyada almashdi.
- O'qituvchi izohlari **4 ta qat'iy bo'limga** ajratilgan: Maqsad · Nima
  deyish kerak · Sinfdan so'rang · Javob.
- Slayd almashganda hech qanday HTTP so'rov yuborilmaydi — holat
  WebSocket orqali uzatiladi (§9).
- Monitor **yorug' temada** qoladi. Qorong'i "canvas" palitrasi faqat
  o'quvchi ilovasida ishlatiladi (§10).

---

## 4. Amaliyot monitori

Oldingi taxmin ("har bola uchun yo'lakcha") noto'g'ri chiqdi. **Yo'lakcha
(lane) — topshiriq**, bola esa chip sifatida o'zi turgan topshiriq qatorida
ko'rinadi:

```
● JONLI · 09:43 DAVOM ETMOQDA            ← darsdan beri o'tgan vaqt

E'TIBORINGIZ KERAK  [● FAMILIYA - boshqa varaqda] [● FAMILIYA - 4 urinish]

[Barchasi 16] [Qo'llar ko'tarilgan 0] [Yordam kerak 1]
[Varaqalar almashtirildi 1] [Oflayn 3]

KUTYAPMIZ 13 ⓘ
 1 Uy qatori         ▬▬▬▬▬▬░░░░  [FAMILIYA] [FAMILIYA] ...
 2 Qaysi qo'l bilan  ▬░░░░░░░░░  [FAMILIYA]
 3 Yuqori qator      ░░░░░░░░░░  Bu yerda hech kim yo'q
 ...
11 Men uchun tugat   ░░░░░░░░░░  Bu yerda hech kim yo'q

HAMMASINI BAJARDI - KUTYAPTI ⓘ
Tarmoqda yo'q: FAMILIYA, FAMILIYA

[O'quvchilar PIN kodi ⌄]   [✋ Diqqat]   [Davom etish →]
```

- Qatordagi chiziq — **histogramma**: shu topshiriqda *hozir* turgan bolalar
  ulushi (maxraj — faol bolalar). Bo'sh qatorda minimal 4%. Masalan
  09:40 da 14 boladan 8 tasi 7-topshiriqda (57%) edi — tor joy darrov ko'rinadi.
- Chiplarda faqat **familiya**. Ko'k — oddiy, qizil — e'tibor kerak.
- Har bola uchun **"Sinfga ko'rsatish"** tugmasi — bolaning ekranini
  proyektorga chiqarish (`mirror-pane`).
- Bu darsda 11 topshiriq: klaviatura qatorlari, katta harf, Caps Lock,
  sonlar, faylga nom berish va hokazo.

### E'tibor signallari

| Signal | Chegara | Filtr | Token |
|---|---|---|---|
| `bitta ekranda N daq` | **2 daqiqa** bitta topshiriqda | Yordam kerak | `idle` |
| `N urinish` | **3 urinish**dan boshlab | Yordam kerak | — |
| `boshqa varaqda` | Bola brauzer tabini almashtirdi | Varaqalar almashtirildi | — |
| Oflayn | Ulanish uzildi | Oflayn + "Tarmoqda yo'q" | `away` |
| Qo'l ko'tarish | Bola o'zi bosadi | Qo'llar ko'tarilgan | `hand` |

- "Yordam kerak" = idle va urinish signallari yig'indisi. Uni tizim
  avtomatik hisoblaydi, bola hech narsa bosmaydi.
- **Tab almashtirishni aniqlash:** bola boshqa tabga o'tsa, o'qituvchi
  darhol ko'radi. Tabga qaytgach, signal o'chadi.
- Soni 0 bo'lgan "Oflayn" filtri ko'rinmay qoladi.
- Kuzatilgan maksimumlar: 5 urinish, 8 daqiqa bitta ekranda.
- Bu darsda hech kim qo'l ko'tarmadi (hisoblagich doim 0).

---

## 5. O'yin maydoni

O'qituvchi "Davom etish" ni bosgach, ekranda faqat **Darsni yakunlash** va
**Viktorinani boshlash** qoldi. O'qituvchi darhol viktorinaga o'tdi, shuning
uchun bu qadamning ichi ko'rilmadi. Shu paytda amaliyotni 13 bola hali
tugatmagan edi — ya'ni keyingi qadamga o'tish hammani kutmaydi.

---

## 6. Viktorina

- Yorliq **YAKUNIY VIKTORINA** + `8 savoldan N-si`
- Taymer — chiziq + raqam, **45 soniya**dan teskari sanaydi
- `Javob berdi: 14 dan N` — real vaqtda o'sadi
- 4 ta katta javob kartochkasi, har biri rang **va** shakl bilan:
  ▲ havorang · ◆ to'q ko'k · ● sariq · ■ qizil (Kahoot uslubi — rangni
  ajrata olmaydigan bola ham shakl bo'yicha topadi)
- **Javoblarni ko'rsatish** — o'qituvchi taymerni kutmay ochishi mumkin
  (bir savolda 14 dan 5 javobda ochildi)

Ochilgandan keyin kartochkalar o'rnida **ustunli diagramma** chiqadi: har
variant uchun ustun va son. To'g'ri javob o'z rangida ✓ bilan, noto'g'rilari
xira. Savol ostida to'g'ri javob alohida belgi bo'lib chiqadi. Tugma
**Keyingi savol**ga almashadi, oxirgi savoldan keyin esa **Viktorina yakuni**ga.

Har savolga ~25–40 soniya ketdi.

---

## 7. Viktorina g'oliblari

`VIKTORINA YAKUNLANDI · Viktorina g'oliblari` — 3 o'rinli podium:
avatar, medal, to'liq F.I.Sh., `{N} ball`, `8 dan N`.

**Ball tezlikka bog'liq:** ikki bola ham 8 dan 5 ta topgan, lekin ballari
har xil (4282 va 4165).

Tugmalar: **Barcha natijalar** · **Darsni yakunlash**.

---

## 8. Dars yakuni — majburiy chiqish

Podiumdan keyin o'qituvchi paneli **kirish sahifasiga otib yuborildi**.
Tarmoq yozuvlari:

```
09:44:12  oxirgi muvaffaqiyatli HTTP so'rov (keyin 4 daqiqa faqat WebSocket)
09:48:43  /organizations/{id}/feedback            → 401
09:48:57  /me, /classes, /organizations/{id}/me   → 401 (×8)
09:48:59  → /login
```

`/auth/logout` chaqirilmagan — o'qituvchi o'zi chiqmagan. Batafsil:
[06-kamchiliklar.md](06-kamchiliklar.md) ⑩.

Shu sababli "Darsni yakunlash" nima so'rashi va `LessonFinale` ekrani
ko'rilmay qoldi.

---

## 9. Real vaqt texnologiyasi

Monitor dars davomida **hech qanday HTTP polling qilmaydi**. Statik JS
bundle tahlili:

- Kutubxona — **Phoenix Channels** mijozi: `phx_` xabarlari, heartbeat
  **30 s**, `rejoinAfterMs`, uzilsa **LongPoll**ga tushadi. Ya'ni backendning
  real vaqt qismi **Elixir / Phoenix** da.
- Endpoint: `/socket`, kanal: `session:{id}`

| Yo'nalish | Eventlar |
|---|---|
| Server → o'qituvchi | `session:started` `session:ended` `current_activity` `attention` `interlude` `screen_position` `events` `activity_replay` `progress` `connection` `hand` `playground` `presence_state` `presence_diff` `mirror_replay` `mirror_event` `mirror_raw` |
| O'qituvchi → server | `acknowledge_hand` `evict_student` `start_mirror` `stop_mirror` `event` `open_activity` `open_interlude` `close_interlude` |

Bundan kelib chiqadi:

- **Kim onlayn** — Phoenix Presence (`presence_state` / `presence_diff`)
- **Ekranni ko'rsatish video emas** — bolaning harakatlari event oqimi
  sifatida qayta o'ynatiladi (`mirror_event`, `mirror_raw`, `mirror_replay`)
- O'qituvchi qo'l ko'tarishni **tasdiqlaydi** (`acknowledge_hand`)
- O'qituvchi bolani **darsdan chiqara oladi** (`evict_student`) — UI da
  ko'rilmadi
- `interlude` — asosiy oqimdan tashqari faoliyat, ehtimol O'yin maydoni

### Sessiya obyekti

`/api/v1/sessions/live` qaytaradigan maydonlar: `status` · `started_at` ·
`current_activity_position` · `interlude_activity_position` ·
`attention_until` · `join_code` · `module_title` · `lesson_title` ·
`class_name` · `roster_size` · `false_start_spent` (+ ID'lar).

`current_activity_position` — joriy qadam raqami (Taqdimotda 1,
Amaliyotda 2). `attention_until` — "Diqqat" rejimi vaqt bilan cheklangan.
`false_start_spent` — "Sessiyani bekor qilish" bilan bog'liq bir martalik
imkoniyat bo'lsa kerak.

### Boshqa API

REST: `https://api.luwo.ai/api/v1/…` — `/me`, `/auth/login`,
`/community-impact`, `/organizations/{id}/{me|classes|feedback}`,
`/classes/{id}/roster`, `/students/{id}/{lessons|skills|summary}`,
`/sessions/{id}`, `/sessions/{id}/monitor`, `/content/scenes/{sha256}`
(kontent hash bo'yicha manzillangan).

Front-end marshrutlari fayl asosida (`_authed.index`, `_authed.classes.index`
kabi chunk nomlari — TanStack Router uslubi).

Analitika: **PostHog (EU)**, jumladan `/s/` — sessiya yozuvi (session replay).

### Mashq muhitlari

Prefetch qilingan komponentlar nomlari mashqlar brauzer ichidagi
**simulyatsiyalar** ekanini ko'rsatadi: OS ish stoli, Office, Word, Paint,
Terminal, veb-qidiruv, jadval, blok dasturlash va hokazo (40+ `*View`).
Tekshiruv kalitlaridan misollar: xat yozishda `greeting`, `signature`,
`shouting` (KATTA HARF bilan "baqirish"); jadvalda `expected_sort`,
`require_formula_cells`; blok dasturlashda `goal_reached`,
`used_required_blocks`.

---

## 10. O'quvchi ilovasi — kirish ekrani

`student.luwo.ai` faqat kirish ekranigacha ko'rildi:

- **Qorong'i tema**, maskot robot. Til bu safar **ruscha** ochildi
  (o'qituvchi paneli inglizcha ochilgan edi)
- Ikki rejim: **В классе** (jonli dars) va **Дома** (uy vazifasi)
- Jonli dars kodi — **6 xonali**, uy vazifasi kodi — **8 xonali**
- Ekranda raqamli klaviatura (0–9, "Очистить", ⌫) — fizik klaviatura
  shart emas
- Shu brauzerda o'qituvchi sessiyasi ochiq bo'lsa, "В классе" rejimida
  ogohlantirish chiqadi: *"На этом компьютере активна сессия учителя…
  используйте режим инкогнито"*. "Дома" rejimida chiqmaydi.

---

## 11. Global banner

Dars ketayotganda o'qituvchi boshqa sahifaga o'tsa, tepada banner turadi:
**"{sinf} — dars ketmoqda · Darsni kuzatishga qaytish"**. Kuzatilgan darsda
o'qituvchi ikki marta `/roster` ga o'tdi (PIN unutgan bola uchun), garchi
monitorning o'zida ham "O'quvchilar PIN kodi" tugmasi bo'lsa ham.
