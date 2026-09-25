# 03 — Dars oqimi

Platformaning yuragi. Uchta alohida oqim bor: **tayyorgarlik**, **jonli dars**,
**uy vazifasi**.

---

## 1. Darsga tayyorlanish (o'qituvchi uchun)

Sinf sahifasidagi **"Darsga tayyorlanish"** tugmasi to'liq ekranli oynani ochadi.

Yuqori panelda: **Mundarija** tugmasi · "TAYYORLANING" yorlig'i · dars nomi ·
`13 slayd` · `5 savol` belgilari · yopish tugmasi.

Pastki panelda: Orqaga · `beyond_coding` (build belgisi) · joriy bosqich
("3 dan 2") · Keyingi.

### Tuzilishi — 3 bosqich

```
1. Brifing      (5 qadam)   — o'qituvchi uchun metodik yo'riqnoma
2. Taqdimot     (13 slayd)  — bolalarga ko'rsatiladigan slaydlar + eslatmalar
3. Viktorina    (5 savol)   — javoblari belgilangan holda
```

Mundarija yon panelidan istalgan slaydga sakrash mumkin.

### 1.1 Brifing

Har qadam alohida mavzuga bag'ishlangan. 1-darsda kuzatilgan qadamlar:

| Qadam | Sarlavha | Mazmuni |
|---|---|---|
| 1 | **O'qituvchi uchun brif** | Darsning **asosiy maqsadi** alohida ta'kidlangan blokda. Misol: *"Yangi bilim emas, mustaqillik"* — ko'p yangi bilim berish emas, bolani platformadan o'zi foydalanishga o'rgatish |
| ... | Dars davomida bola o'rganadi | Aniq, o'lchanadigan ko'nikmalar ro'yxati (sichqonchani yurgizish, chap tugma bilan chertish, klaviaturadan raqamlarni topish, ro'yxatdan o'z ismini topish, PIN kiritish) |
| 3 | **O'qituvchi nimaga e'tibor beradi** | ⚠️ *"Nega bu tez bo'lmaydi"* — ogohlantirish bloki: "Ko'pchilik uchun bu sichqoncha va klaviatura bilan birinchi tanishuv. Shoshirmang." <br> 👁 *"Ayniqsa quyidagilar qiyin bo'lgan bolalarni kuzating"* — aniq qiyinchiliklar ro'yxati |

> Bu — platformaning eng kuchli g'oyalaridan biri. Tayyor kontent berish
> oson, lekin **o'qituvchiga "nimaga qarash kerak"ligini aytish** —
> metodik qiymat aynan shu yerda.

### 1.2 Taqdimot

13 ta slayd. Har slaydda:

- Slayd tasviri (bolalar ko'radigan ekran)
- **"O'QITUVCHI ESLATMALARI"** bloki — aynan nima deyish kerakligi yozilgan
  (masalan maskot tanishtiruvi: *"Salom, bolalar! Mening ismim Luwo..."*)

### 1.3 Viktorina

5 ta savol. Har savolda:

- Savol matni ("5 SAVOLDAN 1-SAVOL" hisoblagichi bilan)
- Javob variantlari **katta rangli kartochkalar** ko'rinishida, har birida
  geometrik belgi (▲ ◆) — Kahoot uslubi
- To'g'ri javobda ✓ belgisi
- Izoh: *"Belgi to'g'ri javobni ko'rsatadi. U faqat sizning ekraningizda —
  bolalarga yuborilmaydi."*

### ⚠️ Muhim kamchilik

Mundarijada faqat **3 bo'lim** bor. **Mashq (amaliyot) qismi tayyorgarlik
oynasida umuman ko'rsatilmaydi** — o'qituvchi bolalar bajaradigan
topshiriqlarni oldindan ko'ra olmaydi. Ular faqat natijalar jadvalida
"7 tadan 3 ta" ko'rinishida paydo bo'ladi.

---

## 2. Jonli dars

> Bu oqim to'g'ridan-to'g'ri kuzatilmagan (dars boshlanmadi — bolalar
> ekraniga chiqadi va yozuv qoldiradi). Quyidagilar o'qituvchi tajribasi va
> kod tahlilidan yig'ilgan.

### Qadamlar

```
1. O'qituvchi "Darsni boshlash" ni bosadi
        ↓
2. Ekranda DARS KODI chiqadi  (uy vazifasi kodidan alohida)
        ↓
3. O'quvchilar student.luwo.ai da "Dars" bo'limini tanlaydi
        ↓
4. Kodni kiritadi  →  SINF RO'YXATI chiqadi
        ↓
5. Har bola ro'yxatdan o'z ismini topib bosadi
        ↓
6. O'z PIN kodini teradi  →  darsga qo'shiladi
        ↓
7. KUTISH XONASI — o'qituvchi kim kirganini real vaqtda ko'radi
   (nechtadan nechta qo'shildi)
        ↓
8. Hammani kutish shart emas — o'qituvchi xohlagan paytda boshlaydi
        ↓
9. MONITOR — dars davomida barcha o'quvchilar holati kuzatiladi
```

### Ikki bosqichli kirish

Bolalar uchun **parol yo'q**. Kirish ikki qismdan iborat:

| Qism | Nima | Kim biladi |
|---|---|---|
| Sinf kodi | Har dars uchun (jonli) yoki o'zgarmas (uy vazifasi) | Butun sinf |
| Shaxsiy PIN | 4 xonali | Faqat bola |

Ism esa yozilmaydi — **ro'yxatdan tanlanadi**. Ya'ni 1-sinf bolasi ham
hech narsa yozmasdan kira oladi (faqat raqamlar).

### Monitor ekranidagi holatlar

CSS tokenlaridan aniqlangan (`docs/05-dizayn-tizimi.md` ga qarang) — jonli
darsda quyidagi holatlar ko'rsatiladi:

| Token | Rang | Taxminiy ma'no |
|---|---|---|
| `hand` | `#f97316` to'q sariq | Qo'l ko'tarish — yordam so'ramoqda |
| `away` | `#574cc4` binafsha | Chiqib ketgan / ulanmagan |
| `pending` | `#64748b` kulrang | Kutilmoqda |
| `idle` | `#bcc4d2` och kulrang | Harakatsiz — qotib qolgan |
| `done` | `#4cb85f` yashil | Bajardi |
| `correct` / `incorrect` | `#46d6a4` / `#ff6f91` | To'g'ri / noto'g'ri javob |
| `cell-current` | `#7ac8f5` | Joriy qadam |

Har bir o'quvchi uchun alohida **"lane"** (yo'lakcha) uslublari mavjud:
`lane-head`, `lane-rule`, `lane-gap` — ya'ni monitor gorizontal yo'laklar
ko'rinishida, har bolaning dars bo'ylab harakati ko'rinadi.

Shuningdek `mirror-pane` tokeni bor — ehtimol o'qituvchi bolaning ekranini
"ko'zgu" qilib ko'ra oladi.

### Dars tuzilishi

```
TAQDIMOT  →  MASHQ (amaliyot)  →  SAVOL (viktorina)
```

Natijalar shu uch qismga mos yozib boriladi: topshiriqlar soni, taxminiy
ball, viktorina natijasi.

---

## 3. Uy vazifasi

Jonli darsdan mustaqil oqim.

```
1. Sinfning O'ZGARMAS uy kodi bor (sinf sahifasida ko'rinadi)
        ↓
2. Bola uyda student.luwo.ai ni ochadi
        ↓
3. "Uy vazifasi" ni tanlaydi
        ↓
4. Kod → o'z ismi → PIN
        ↓
5. Hali o'tmagan darsni boshlaydi
   YOKI tugatmagan darsini davom ettiradi
```

Ikki kod tizimi farqi:

| | Jonli dars kodi | Uy vazifasi kodi |
|---|---|---|
| Qayerda | Dars boshlanganda ekranda | Sinf sahifasida doimiy |
| O'zgaradimi | Har dars uchun yangi | O'zgarmas |
| Vazifasi | Sinxron dars | Mustaqil ish |

---

## Kuzatilgan holat: tugallanmagan dars

Tadqiqot paytida bir sinfda dars **ochiq qolgan** edi: 20 o'quvchidan 17 tasi
"Tugatilmadi" holatida, natijalar oraliq ko'rinishda ("Dastlabki natija: dars
hali tugamagan"), va sinf tili tanlagichi bloklangan edi.

Ya'ni **dars aniq yakunlanishi kerak** — aks holda:

- Natijalar oraliq holatda qoladi
- Ko'nikmalar hisobga olinmaydi (tugatilmagan dars ko'nikma bermaydi)
- Sinf sozlamalari qulflanadi

Bu mahsulot dizaynidagi muhim jihat: dars — bu **sessiya**, uning boshi va
oxiri bor.
