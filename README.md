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

**Qolgan:**

- [ ] **Jonli dars ekrani** — eng muhim qism, hali ochilmagan
- [ ] Kutish xonasi (lobby) interfeysi
- [ ] O'quvchi tomoni (`student.luwo.ai`)
- [ ] Mashq/amaliyot topshiriqlarining ichki tuzilishi
- [ ] PIN kartochkalarini chop etish ko'rinishi
- [ ] "Boshqa sinfga o'tkazish" oqimi
- [ ] Til almashtirish xatti-harakati

---

## Metodologiya

Tadqiqot brauzer orqali olib borildi: sahifalar DOM va accessibility daraxti
sifatida o'qildi, CSS build fayli (`index-*.css`, ~367 KB) to'liq tahlil qilindi,
kontrast koeffitsientlari WCAG formulasi bo'yicha hisoblandi, responsive
xatti-harakat 375px / 768px / desktop kengliklarida sinaldi.

**Tegilmagan amallar:** jonli dars boshlanmadi (o'quvchilar ekraniga chiqadi va
yozuv qoldiradi), o'quvchilar boshqa sinfga ko'chirilmadi, PIN kodlar ochilmadi,
sozlamalar o'zgartirilmadi.

---

## Maxfiylik

Bu repozitoriyda **hech qanday shaxsiy ma'lumot yo'q**: o'quvchilar ismlari,
PIN kodlari, sinfga kirish kodlari, maktab nomi va hisob ma'lumotlari
ataylab kiritilmagan. O'quv dasturi ham modul darajasida tavsiflangan —
Luwo'ning dars kontenti to'liq ko'chirilmagan.
