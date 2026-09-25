# 05 — Dizayn tizimi

CSS build fayli (`assets/index-*.css`, ~367 KB) to'liq tahlil qilindi.

---

## 1. Texnik asos

**Tailwind CSS v4** + custom `@theme` qatlami. Vite build, bitta CSS fayl.

Muhim kuzatish: **custom komponent klasslari umuman yo'q** — hech qanday
`.btn`, `.card`, `.nav-item` kabi BEM klasslar topilmadi. 100% utility-first.
Komponentlar React darajasida, uslublar esa faqat Tailwind utility'lari orqali.

Jami **343 ta CSS o'zgaruvchisi**, shundan **194 tasi custom** (qolgani —
Tailwind'ning standart `oklch` palitrasi).

---

## 2. Ranglar

### Brend shkalasi (9 pog'ona)

```
brand-50   #f2f9ff    eng och fon
brand-100  #e2f3ff
brand-200  #b2deff
brand-300  #7ac8f5
brand-400  #01c3ff    yorqin akцent (hover)
brand-500  #16abd9    asosiy brend rangi
brand-600  #1188b4    focus ring
brand-700  #235479
brand-800  #19284c
brand-900  #121d39    to'q siyoh (matn, qora tugma)
```

### Semantik tokenlar

| Token | Qiymat | Vazifa |
|---|---|---|
| `bg` | `#f7f9fc` | Sahifa foni (sovuq oq) |
| `fg` | `#111a3c` | Asosiy matn |
| `fg-soft` | `#3c4761` | Yumshoq matn |
| `card` | `#ffffff` | Kartochka foni |
| `border` | `#e2e6ee` | Hoshiya |
| `border-subtle` | `#edf0f5` | Eng nozik hoshiya |
| `muted` / `muted-fg` | `#eef1f6` / `#56617d` | Ikkilamchi fon va matn |
| `meta` | `#8b95ab` | Jadval sarlavhalari |
| `faint` | `#9ba5b8` | Eng och matn |
| `ring` | `#1188b4` | Fokus halqasi |
| `primary` / `primary-hover` | `#16abd9` / `#01c3ff` | Asosiy tugma |
| `action-dark` / `hover` | `#121d39` / `#19284c` | Qora tugma |
| `danger` / `deep` / `tint` | `#e5533d` / `#cf4123` / `#fdeeeb` | Xato |
| `success` | `#16a34a` | Muvaffaqiyat |
| `warn` / `deep` / `mid` / `tint` | `#e0a012` / `#a07408` / `#b6820c` / `#fcf8ee` | Ogohlantirish |
| `done` / `deep` / `tint` | `#4cb85f` / `#35a34a` / `#edf9ee` | Bajarildi |
| `track` | `#e8edf4` | Progress yo'lakchasi |

Har bir semantik rang uchun **uchta variant** bor: asosiy, `deep` (to'q — matn
uchun) va `tint` (och — fon uchun). Bu yaxshi tizimli yondashuv.

### Sinf darajasi shkalasi

```
grade-1  #e8f5ff   →   grade-9  #121d39
```

`#e8f5ff` · `#b7daf1` · `#82c0e2` · `#3ba6d4` · `#0090c9` · `#006fa0` ·
`#00527c` · `#083759` · `#121d39`

Yosh ulg'aygan sari rang to'qlashadi — 1-sinf och osmoniy, 9-sinf deyarli qora.
Nozik va o'ylangan detal.

### Ikkinchi tema — jonli dars rejimi

Butunlay alohida, **qorong'i** palitra:

| Token | Qiymat |
|---|---|
| `canvas` | `#0f172a` |
| `surface` | `#1e293b` |
| `elevated` | `#334155` |
| `line` | `#475569` |
| `ink` / `ink-muted` | `#f1f5f9` / `#94a3b8` |
| `brand` | `#22d3ee` (neon cyan) |
| `brand-ink` | `#082f49` |
| `correct` / `incorrect` | `#46d6a4` / `#ff6f91` |
| `active` | `#ffd166` |
| `pending` | `#64748b` |

O'zining radius shkalasi bilan: `key .625rem` · `tile .875rem` · `panel 1.5rem`.
"Key" nomi klaviatura tugmasi yoki javob kartochkasini anglatadi.

### Monitor holat ranglari

`hand #f97316` (qo'l ko'tarish) · `away-mid #574cc4` va `chip-away #f0eefc`
(chiqib ketgan) · `idle #bcc4d2` · `cell-current #7ac8f5` ·
`mirror-pane #f5fafe` · `lane-head #f8fbfe` · `lane-rule #eff3f8` ·
`lane-gap #fafcfe` · `danger-row #fdf3f0`.

---

## 3. Tipografika

### Shriftlar

| Rol | Shrift | Og'irliklar |
|---|---|---|
| Sarlavhalar | **Wix Madefor Display Variable** | 400–800 |
| Matn | **Wix Madefor Text Variable** | 400–800 |
| Monospace | **Geist Mono Variable** | 100–900 |

Har biri to'rt subset bilan: `latin`, `latin-ext`, **`cyrillic`**, `vietnamese`.
Qo'shimcha: har shriftning kichik **base64 inline** varianti ham bor — birinchi
renderda matn "sakramasligi" (FOUT) uchun.

### Maxsus o'lcham shkalasi

Tailwind'ning standart `text-sm/base/lg` shkalasidan tashqari, piksellarda
aniq sozlangan o'z shkalasi:

```
card-title  18px
body        16px
list        15.5px
secondary   15px
sublabel    14px
label       13.5px
micro       13px
nano        12px
```

15.5 va 13.5 kabi yarim piksellar — juda nozik sozlash.

### Amaldagi qiymatlar

| Element | O'lcham | Og'irlik | Shrift | Qo'shimcha |
|---|---|---|---|---|
| H1 | 24px | 700 | Display | `tracking-tight` (−0.6px) |
| H2 | 18px | 600 | Display | |
| Body | 16px | 400 | Text | `line-height: 24px` |
| Jadval sarlavhasi | 13px | 600 | Text | `uppercase`, `letter-spacing: 0.52px` |
| Nav element | 16px | 500 | Text | |

---

## 4. Geometriya

### Radius

```
control       8px     tugma, input
popover      14px     ochiluvchi panel
card         20px     kartochka
nav item     12px     yon menyu bandi
```

### Soya — butun tizimda bitta

```css
0 1px 2px rgba(17, 26, 60, 0.04),
0 18px 34px -30px rgba(17, 26, 60, 0.4)
```

Juda yumshoq, katta tarqalishli, deyarli ko'rinmas. Elementlar "suzib turgandek"
his beradi. Qattiq/quyuq soya umuman ishlatilmagan.

### Spacing va konteyner

- Asosiy birlik: `0.25rem` (4px)
- Amaldagi gaplar: 2 / 6 / 8 / 12 / 16px
- Sahifa konteyneri: `max-width: 80rem` (1280px), markazlashtirilgan
- Main padding: `px-4 pt-5 pb-16` → `md:px-10 md:pt-[46px] md:pb-[90px]`

---

## 5. Komponentlar

### Tugma

```
inline-flex items-center justify-center whitespace-nowrap
rounded-control font-medium transition-colors outline-none
focus-visible:ring-2 focus-visible:ring-ring
disabled:pointer-events-none
```

| Variant | Fon | Matn | Padding |
|---|---|---|---|
| Primary | `#16abd9` | oq | `0 28px` |
| Ghost | oq + 0.8px hoshiya | `#111a3c` | `0 20px` |
| Action-dark | `#121d39` | oq | — |

### Kartochka

```
rounded-card border border-border bg-card text-card-fg shadow-card
p-5 sm:p-6
```

Radius 20px, hoshiya 0.8px `#e2e6ee`, padding 20→24px.

### Ikonlar

**Lucide** kutubxonasi. Barchasi `24×24` viewBox, `stroke-width: 2`,
`stroke: currentColor`, `fill: none`. O'lcham utility bilan beriladi:
`size-[18px]`, `size-[22px]`.

### Jadval

`table-fixed border-collapse` + `min-w-[700px]` (gorizontal scroll bilan).
Lekin `/classes` sahifasida jadval emas — **CSS Grid** ishlatilgan
(shu sababli mobil nosozlik yuz bergan).

---

## 6. Responsive

### Breakpointlar

Standart: `40rem` (640) · `48rem` (768) · `64rem` (1024) · `80rem` (1280) ·
`96rem` (1536)

Maxsus: `560px` · `860px` · `900px` · `1180px`

### Layout o'zgarishi

| Kenglik | Yon menyu | Header |
|---|---|---|
| `< 768px` | Off-canvas drawer (`fixed`, `transition-transform 300ms`) | 61px sticky header + hamburger |
| `≥ 768px` | Doimiy sticky sidebar **236px**, yig'ish tugmasi bilan | Yo'q (`md:hidden`) |

Sidebar: `h-dvh`, oq fon, o'ng tomonda 0.8px hoshiya, `print:hidden`.
Qatlamlarni boshqarish uchun `--shell-top` CSS o'zgaruvchisi ishlatiladi.

Gorizontal overflow yo'q — `overflow-x-clip` va dekorativ doiralar to'g'ri
kesilgan.

---

## 7. Harakat

### Keyframe'lar (19 ta)

Umumiy: `spin` · `ping` · `pulse` · `bounce` (Tailwind standarti)

Dars rejimi uchun (15 ta, `l` prefiksi bilan):
`lsheet-in` · `lsheet-out` · `lscrim-in` · `lscrim-out` · `lscrim` ·
`lpulse` · `lglow` · `lflash` · `lslide-from-past` · `lslide-from-recent` ·
`lfade` · `ldrawer` · `lpop` · `lcheck` · `lcaret`

`lslide-from-past` va `lslide-from-recent` — slaydlar yo'nalishga qarab
turlicha kirib keladi. `lcheck` — javob belgilanganda, `lglow`/`lflash` —
diqqat tortish, `lcaret` — matn kursori.

### Davomiyliklar

`75` · `100` · `150` · `200` · `300` · `500` · `700` · `1000` ms

Default: `150ms cubic-bezier(.4, 0, .2, 1)`

### Micro-interaksiyalar

- Hover: `-translate-y-0.5` / `-translate-y-1` (ko'tarilish), `scale-105`,
  `translate-x-[3px]`, hoshiya rangi almashinuvi — jami **148 xil hover holati**
- Bosilganda: `active:scale-95` yoki `active:scale-90`
- Raqamlar: slot-mashina uslubida (`translateY(-26em)` bilan 0–9 ustuni)

### Reduced motion

`prefers-reduced-motion` **to'liq qo'llab-quvvatlanadi**:
`motion-safe:` va `motion-reduce:` variantlari orqali animatsiyalar,
transitionlar, hover ko'tarilishi va scale effektlari o'chiriladi.

---

## 8. Accessibility

Kutilganidan ancha puxta:

| Jihat | Holat |
|---|---|
| Landmark'lar | ✅ `header`, `aside`, `nav`, `main` to'g'ri ishlatilgan |
| Sarlavhalar ierarxiyasi | ✅ H1 → H2, sakrash yo'q |
| Rasmlar `alt` | ✅ Barchasida bor |
| Tugmalar nomi | ✅ Ikonli tugmalarda ham `aria-label` bor |
| Progress halqasi | ✅ `role="meter"` |
| Animatsion raqamlar | ✅ `aria-hidden="true"` + yoniga `.sr-only` haqiqiy qiymat |
| Fokus ko'rinishi | ✅ `focus-visible:ring-2` (`#1188b4`) |
| Radiogroup'lar | ✅ To'g'ri `radiogroup`/`radio` rollari |
| Reduced motion | ✅ To'liq |
| **Rang kontrasti** | ❌ **Muammo bor** — [06-kamchiliklar.md](06-kamchiliklar.md) |

---

## 9. Boshqa detallar

- **Dark mode:** `@media (prefers-color-scheme: dark)` bloki bor, lekin atigi
  ~23 ta utility (sky/slate/emerald). Tizimli qorong'i tema yo'q.
- **Print:** atigi 4 ta qoida (`print:hidden`, `print:block`, `print:flex`).
- **Scrollbar:** `scrollbar-width` sozlangan.
- **Tap highlight:** mobil uchun boshqarilgan.
- **`safe-area-inset`:** ishlatilmagan (iPhone pastki zonasi).
- **`will-change`:** ishlatilgan (animatsiya optimizatsiyasi).
- **Scroll snap:** ishlatilmagan.
