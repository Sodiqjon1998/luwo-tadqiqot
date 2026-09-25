# Luwo platformasi — tadqiqot

`teacher.luwo.ai` o'qituvchi panelini ikir-chikirigacha o'rganish.

Bu repozitoriy — davom etayotgan tadqiqot daftari. Har bir yangi kashfiyot
tegishli faylga qo'shib boriladi.

---

## Mundarija

| Fayl | Mazmuni |
|---|---|
| [01 — Platforma](docs/01-platforma.md) | LUWO nima, ko'lami, standartlar, uch qismli tuzilishi |
| [02 — Sahifalar xaritasi](docs/02-sahifalar.md) | O'qituvchi panelining har bir sahifasi va elementi |
| [03 — Dars oqimi](docs/03-dars-oqimi.md) | Tayyorgarlik, jonli dars, uy vazifasi — qadamma-qadam |
| [04 — O'quv dasturi](docs/04-oquv-dasturi.md) | Modul/dars tuzilishi, sinflar bo'yicha farqlar |
| [05 — Dizayn tizimi](docs/05-dizayn-tizimi.md) | Tokenlar, ranglar, tipografika, responsive, animatsiya |
| [06 — Kamchiliklar](docs/06-kamchiliklar.md) | Topilgan nosozliklar va kontrast muammolari |
| [07 — Ochiq savollar](docs/07-ochiq-savollar.md) | Hali tekshirilmagan joylar — keyingi qadamlar |
| [08 — Jonli dars](docs/08-jonli-dars.md) | Haqiqiy dars kuzatuvi: lobby, monitor, viktorina, real vaqt protokoli |

**Tadqiqot asosidagi loyiha:** [SQL Maktab — MVP rejasi](mvp/sql-maktab-mvp.md) —
9–11-sinflar uchun LUWO uslubidagi SQL o'qitish platformasi (Python + PostgreSQL).

---

## Tadqiqot holati

**O'rganilgan:**

- [x] Marketing sayti (`luwo.ai`) — pozitsiyalash, ko'lam, standartlar
- [x] Kirish sahifasi va autentifikatsiya oqimi
- [x] Bosh sahifa (dashboard) ko'rsatkichlari
- [x] Sinflar ro'yxati va sinf detali sahifasi
- [x] O'quv dasturi sahifasi (1-sinf va 8-sinf solishtirildi)
- [x] O'quvchilar ro'yxati va individual hisobot sahifasi
- [x] Yordam/murojaat tizimi
- [x] "Darsga tayyorlanish" oynasi (Brifing → Taqdimot → Viktorina)
- [x] Dizayn tizimi — CSS tokenlari darajasida
- [x] Responsive xatti-harakat (375 / 768 / desktop)
- [x] Accessibility auditi
- [x] **Jonli dars ekrani** — lobby, taqdimot, amaliyot monitori, viktorina, podium
- [x] Kutish xonasi (lobby) interfeysi
- [x] Real vaqt texnologiyasi — Phoenix Channels (WebSocket)

**Qisman:**

- [ ] O'quvchi tomoni (`student.luwo.ai`) — faqat kod kiritish ekrani
- [ ] Mashq/amaliyot topshiriqlarining ichki tuzilishi — faqat monitor va kod nomlaridan
- [ ] Dars yakuni — "Darsni yakunlash" dialogi va `LessonFinale` ko'rilmadi
- [ ] Til almashtirish xatti-harakati — boshlang'ich til kuzatildi

**Qolgan:**

- [ ] O'yin maydoni (dars 3-qadami) ichi
- [ ] PIN kartochkalarini chop etish ko'rinishi
- [ ] "Boshqa sinfga o'tkazish" oqimi

---

## Metodologiya

Tadqiqot brauzer orqali olib borildi: sahifalar DOM va accessibility daraxti
sifatida o'qildi, CSS build fayli (`index-*.css`, ~367 KB) to'liq tahlil qilindi,
kontrast koeffitsientlari WCAG formulasi bo'yicha hisoblandi, responsive
xatti-harakat 375px / 768px / desktop kengliklarida sinaldi.

**Jonli dars (2026-09-25):** o'qituvchi haqiqiy darsni o'zi o'tkazdi.
Kuzatuvchi faqat sahifa holatini, DOM'ni, tarmoq so'rovlari vaqtlarini va
statik JS bundle'larni o'qidi. Dars sahifasida hech narsa bosilmadi.

**Tegilmagan amallar:** o'quvchilar boshqa sinfga ko'chirilmadi, sozlamalar
o'zgartirilmadi, jonli darsda "Sinfga ko'rsatish", "Diqqat" va bolani
chiqarish tugmalari bosilmadi.

---

## Maxfiylik

Bu repozitoriyda **hech qanday shaxsiy ma'lumot yo'q**: o'quvchilar ismlari,
PIN kodlari, sinfga kirish kodlari, maktab nomi va hisob ma'lumotlari
ataylab kiritilmagan. O'quv dasturi ham modul darajasida tavsiflangan —
Luwo'ning dars kontenti to'liq ko'chirilmagan.
