# 02 — Sahifalar xaritasi

O'qituvchi panelining to'liq tuzilishi.

```
/                          Bosh sahifa (dashboard)
/classes                   Sinflar ro'yxati
/classes/{id}              Sinf detali — dars boshqaruvi
/curriculum                O'quv dasturi
/roster                    O'quvchilar ro'yxati
/roster/{sinf}/{o'quvchi}  Individual o'quvchi hisoboti
/support                   Yordam va murojaatlar
/forgot-password           Parolni tiklash (autentifikatsiyasiz)
```

---

## Yon menyu (navigatsiya)

| Band | Manzil | Izoh |
|---|---|---|
| Bosh sahifa | `/` | |
| Sinflar | `/classes` | |
| O'quv dasturi | `/curriculum` | |
| Ro'yxat | `/roster` | |
| — ajratuvchi — | | |
| Ko'rsatmalar | — | **Ishlamaydi** — bosilganda hech narsa ochilmaydi |
| Yordam | `/support` | |
| Til tanlash | — | Interfeys tili (sinf tilidan alohida) |
| Profil + chiqish | — | Ism, maktab nomi va chiqish tugmasi |

Yuqori qismda logotip va maktab nomi turadi.

**Xatti-harakat:** `< 768px` da yon menyu off-canvas panel sifatida ochiladi
(ustiga qorong'i fon tushadi), `≥ 768px` da doimiy sticky sidebar bo'lib qoladi
va yig'ish (collapse) tugmasi paydo bo'ladi.

---

## `/` — Bosh sahifa

Sarlavha: sana + maktab nomi, so'ng vaqtga qarab salomlashuv
("Xayrli kech, {ism}").

To'rtta kartochka:

| Kartochka | Mazmuni | Havola |
|---|---|---|
| **Sizning darslaringiz** (to'q) | O'qituvchi o'tkazgan darslar soni | — |
| **Keyingi marra** | Progress halqasi: keyingi bosqichgacha necha dars qolgani | Sinfni tanlash → `/classes` |
| **Hal qilingan murojaatlar** | Yopilgan support ticketlar soni | Murojaatlaringiz → `/support` |
| **Luwo bilan birga** | Platformada o'tkazilgan umumiy darslar soni | — |

Raqamlar slot-mashina uslubida aylanib chiqadi (animatsiya).
Progress halqasi `role="meter"` bilan belgilangan.

O'ng pastda doimiy suzuvchi tugma — **"Muammo haqida xabar bering"** (kalit belgisi).
Bu tugma barcha sahifalarda mavjud.

---

## `/classes` — Sinflar ro'yxati

- Sarlavha: "Mening sinflarim" + umumiy sinflar soni
- **Sinf darajasi filtri:** 1-sinfdan 11-sinfgacha tugmalar qatori (radiogroup)
- Tanlangan darajadagi sinflar jadvali

Jadval ustunlari: **Sinf** · **O'quvchilar** · **Keyingi dars** · **Amaliyot** · (o'q)

> ⚠️ Bu jadval CSS Grid bilan qurilgan va mobil qurilmada buziladi —
> batafsil [06-kamchiliklar.md](06-kamchiliklar.md) da.

---

## `/classes/{id}` — Sinf detali

Eng ko'p funksiyaga ega sahifa. Uch qismdan iborat:

### A. Sarlavha

- Orqaga havola ("Barcha sinflar")
- Sinf nomi, o'quvchilar soni, fan, sinf darajasi
- **Sinf tili** tanlagichi — bolalar kontentni qaysi tilda ko'rishi
  - Dars davom etayotganda **bloklanadi**: *"Dars davomida tilni o'zgartirib
    bo'lmaydi. Avval darsni tugating."*

### B. Uydagi darslar

- Katta raqamli **uy vazifasi kodi** (8 xonali, sinf uchun o'zgarmas)
- Uch qadamli yo'riqnoma: kodni bolalarga berish → bola `student.luwo.ai` da
  "Uy vazifasi"ni tanlaydi → kod, ism, PIN kiritadi

### C. Joriy dars bloki

- Dars raqami va nomi, qaysi modulga tegishligi
- **"Darsga tayyorlanish"** — to'liq ekranli tayyorgarlik oynasi
- **"Darsni boshlash"** — jonli darsni ishga tushiradi

### D. Natijalar

Modullar akkordeon ko'rinishida. Har modulda darslar ro'yxati va holati:
`keyingi dars` · `o'tkazilmagan` · `Joriy` · `Boshlanmagan`.

O'tkazilgan dars ochilsa — natijalar jadvali:

| Ustun | Mazmuni |
|---|---|
| O'quvchi | Ism (holat belgisi bilan) |
| Topshiriqlar | "7 tadan 3 ta" ko'rinishida |
| Ball | Taxminiy foiz (≈43) |
| Viktorina | "8 tadan 7 ta" |

Holatlar: **Boshlanmadi** · **Tugatilmadi** · (tugatilgan).
Tugatilmagan darsda izoh chiqadi: *"Dastlabki natija: dars hali tugamagan"*.

---

## `/curriculum` — O'quv dasturi

- Sinf darajasi filtri: **1–8** (sinflar ro'yxatidan farqli — 9–11 yo'q)
- Tanlangan sinf uchun: fan · modullar soni · darslar soni
- Modullar akkordeon, ichida darslar ro'yxati

Har bir dars yonida holat:

| Holat | Ma'nosi |
|---|---|
| **Darsga tayyorlanish** | Ochiq — tayyorgarlik oynasini ochish mumkin |
| **Hozircha yopiq** | Hali ochilmagan (ketma-ket ochiladi) |

Ya'ni o'qituvchi butun yillik dasturni ko'radi, lekin faqat yaqin darslarga
tayyorlana oladi.

---

## `/roster` — O'quvchilar ro'yxati

- Sinf darajasi filtri, so'ng sinf tanlash (1A, 1B, 1V...)
- **"Barcha sinflar uchun PIN kartochkalarini chop etish"** — umumiy tugma

Har bir sinf uchun uchta amal:

| Tugma | Vazifasi |
|---|---|
| Hammasini ko'rsatish | Barcha PIN kodlarni bir vaqtda ochadi |
| PIN kartochkalarini chop etish | Chop etish ko'rinishi |
| Boshqa sinfga o'tkazish | O'quvchini ko'chirish |

O'quvchilar ro'yxatida har bir qator: tartib raqami · avatar (o'zgartirish
mumkin) · F.I.Sh. · **PIN-kod** (yashirin, ko'z belgisi bilan ochiladi) ·
**Amaliyot** ko'rsatkichi.

---

## `/roster/{sinf}/{o'quvchi}` — Individual hisobot

- Breadcrumb: O'quvchilar › Sinf › Ism
- Bolaning ismi, sinfi, fan, yashirin PIN
- **Uchta ko'rsatkich:** tugatilgan darslar (0/9) · tugatilgan modullar (0/1) ·
  tugatilmagan darslar

**Yillik dastur** — har bir dars uchun qator:
sana · amaliyot natijasi · viktorina natijasi · holat.

**Ko'nikmalar** bo'limi — bola egallagan ko'nikmalar. Muhim qoida:
*"Boshlangan, ammo tugatilmagan dars ko'nikma natijasiga qo'shilmaydi."*

---

## `/support` — Yordam

**Yuqori banner:** yuborilgan fikrlar statistikasi — "Qabul qilindi" va
"Foydalanish mumkin" hisoblagichlari.

**Murojaat formasi:**

- Toifa (radiogroup): Nimadir buzilgan · Noto'g'ri yoki tushunarsiz kontent ·
  Hisob yoki kirish · Boshqa narsa
- Matn maydoni: *"Nima qilayotgan edingiz, nimani kutgandingiz va uning
  o'rniga nima bo'ldi"*

**Mening murojaatlarim:** Barchasi / Ochiq / Yopiq filtri +
"Barchasini o'qilgan deb belgilash".

**Shoshilinch yordam:** *"Muammo darsga to'sqinlik qilsa va kuta olmasangiz,
Telegram orqali yozing"* — Telegram ulanishi holati ko'rsatiladi
("Telegram ulangan", qachondan beri) + "Telegram orqali yozish" va
"Qayta ulash" tugmalari.

> Bu yaxshi mahsulot qarori: dars vaqtidagi muammo ticket tizimini kutib
> o'tira olmaydi.

---

## Kirish sahifasi

- Logotip + "O'qituvchi" yorlig'i
- Sarlavha: "С возвращением" / "Xush kelibsiz"
- Email + parol (ko'rsatish/yashirish tugmasi bilan)
- "Сброс пароля" → `/forgot-password`
- Yagona "Kirish" tugmasi

Ro'yxatdan o'tish yo'q — hisoblar markazlashgan holda beriladi.
