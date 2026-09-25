# 06 — Topilgan kamchiliklar

Muhimlik darajasi bo'yicha tartiblangan.

---

## ① Asosiy tugma rangi WCAG kontrastidan o'tmaydi

**Daraja:** yuqori · **Ta'sir:** butun platforma

Kontrast koeffitsientlari (WCAG 2.1 formulasi bo'yicha hisoblangan):

| Kombinatsiya | Kontrast | 16px matn talabi (4.5:1) |
|---|---|---|
| Oq matn / `primary #16abd9` | **2.67:1** | ❌ |
| Oq matn / `primary-hover #01c3ff` | **2.05:1** | ❌ |
| Oq matn / `warn #e0a012` | 2.28:1 | ❌ |
| Oq matn / `success #16a34a` | 3.30:1 | ❌ |
| Oq matn / `danger #e5533d` | 3.73:1 | ❌ |
| `meta #8b95ab` / oq fon | 3.01:1 | ❌ |
| `meta #8b95ab` / `muted #eef1f6` | 2.66:1 | ❌ |
| `faint #9ba5b8` / oq fon | 2.48:1 | ❌ |

Taqqoslash uchun — to'g'ri ishlaydiganlari:

| Kombinatsiya | Kontrast |
|---|---|
| `fg #111a3c` / `bg #f7f9fc` | **16.1:1** ✅ |
| Oq matn / `action-dark #121d39` | **16.66:1** ✅ |
| `muted-fg #56617d` / oq | **6.17:1** ✅ |

**Nima demak:** "Darsni boshlash", "Kirish", "Murojaatni yuborish" kabi barcha
asosiy tugmalar yorqin sinfxonada, quyosh tushgan ekranda yoki proyektorda
o'qilishi qiyin. Hover holatida esa yanada yomonlashadi (2.05:1).

**Yechimlar:**

| Variant | Kontrast | Izoh |
|---|---|---|
| Matnni `#121d39` ga o'zgartirish | 6.2:1 | Fon rangi saqlanadi |
| Fonni `brand-600 #1188b4` ga tushirish | 4.6:1 | Oq matn qoladi |
| `action-dark` ni asosiy tugma qilish | 16.66:1 | Tizimda allaqachon bor |

Diqqatga sazovor: to'g'ri variant tizimda **allaqachon mavjud** —
`action-dark` tokeni 16.66:1 beradi. Ya'ni muammo palitrada emas, tanlovda.

Jonli darsda ham xuddi shu rang ishlatiladi: viktorinadagi **"Keyingi savol"**
va **"Viktorina yakuni"** tugmalari proyektorga chiqadigan ekranda turadi.

---

## ② `/classes` grid'i mobil qurilmada buziladi

**Daraja:** yuqori · **Ta'sir:** telefondan foydalanadigan o'qituvchilar

Sinflar jadvali quyidagi grid bilan qurilgan:

```css
grid-cols-[minmax(0,1.1fr) 104px minmax(0,2.3fr) 148px 16px]
gap-4 px-5
```

Responsive varianti **yo'q** — barcha kengliklarda bir xil.

**Hisob-kitob (375px ekran):**

```
Qat'iy ustunlar:  104 + 148 + 16           = 268px
Gaplar:           16 × 4                   =  64px
Padding:          20 × 2                   =  40px
                                    JAMI   = 372px

Mavjud joy (kartochka ichi):              ≈ 295px
```

372 > 295, shuning uchun ikkala `minmax(0, Xfr)` ustuni **0px ga siqiladi**.

**Natija:** o'qituvchi telefonda sinflar ro'yxatini ochsa, **"Sinf" va
"Keyingi dars" ustunlari butunlay yo'qoladi** — faqat raqamlar qoladi
(`19 —`, `24 —`, `20 —`). Qaysi qator qaysi sinf ekanini aniqlab bo'lmaydi.

**768px (planshet) da ham yaxshi emas:** sinf nomi ustuni atigi **25px**
(`S…` ko'rinishida kesiladi), dars nomi **53px** (`1-dar…`), shu bilan birga
bo'sh "Amaliyot" ustuni **148px** egallab turadi.

**Ildiz sababi:** ustunlar ustuvorligi teskari qo'yilgan — qat'iy kenglikdagi
raqamli ustunlar eng ma'lumotli matn ustunlaridan ustun turibdi.

**Yechim:** mobil uchun grid'ni kartochka ko'rinishiga o'tkazish
(`md:grid-cols-[...]`), yoki qat'iy ustunlarni ham `minmax()` ga o'tkazib,
sinf nomiga eng yuqori ustuvorlik berish.

---

## ③ Dark mode chala qolgan

**Daraja:** o'rta

`@media (prefers-color-scheme: dark)` bloki mavjud, lekin ichida atigi
**~23 ta utility** bor (sky, slate, emerald, amber ranglari) — bu bir-ikki
kichik komponentga yetadi, xolos.

Natija: telefonini qorong'i rejimda ishlatadigan o'qituvchi uchun interfeys
oq bo'lib qolaveradi. Qiziq tomoni — jonli dars rejimi uchun **to'liq
qorong'i palitra allaqachon mavjud** (`canvas`, `surface`, `ink`...), ya'ni
tizimli dark mode uchun asos bor, faqat panelga tatbiq qilinmagan.

---

## ④ "Ko'rsatmalar" menyu bandi ishlamaydi

**Daraja:** o'rta

Yon menyudagi "Ko'rsatmalar" bandini bosganda hech narsa ochilmaydi —
na sahifa, na modal, na tur. Boshqa menyu bandlaridan farqli, bu `<a href>`
emas, `<button>`, lekin hech qanday natija bermaydi.

Ehtimollar: hali ishlab chiqilmagan, faqat birinchi kirishda ko'rsatiladi,
yoki oddiy nosozlik.

---

## ⑤ O'quv dasturi va sinf sahifasi mos kelmaydi

**Daraja:** o'rta

1-sinf, Modul 1:

| Manba | Darslar |
|---|---|
| `/curriculum` | 10 |
| `/classes/{id}` | 9 |

Sinf sahifasida ro'yxat 6-darsdan 8-darsga sakraydi — **7-dars ko'rinmaydi**.
O'qituvchi dasturda ko'rgan darsni sinfida topa olmaydi.

---

## ⑥ Mashq bosqichi tayyorgarlik oynasida yo'q

**Daraja:** o'rta · **Turi:** UX/mahsulot

Dars uch qismdan iborat: **Taqdimot → Mashq → Viktorina**. Lekin
"Darsga tayyorlanish" oynasining mundarijasida faqat **3 bo'lim** bor:
Brifing, Taqdimot, Viktorina.

Ya'ni o'qituvchi darsga tayyorlanayotganda **bolalar bajaradigan
topshiriqlarni oldindan ko'ra olmaydi**. Topshiriqlar faqat dars davomida
va natijalar jadvalida ("7 tadan 3 ta") paydo bo'ladi.

Bu ataylab qilinganmi (o'qituvchi vaqtini tejash) yoki kamchilikmi —
aniqlash kerak. Lekin "nimaga e'tibor berish kerak"ligini shunchalik
batafsil tushuntiradigan platforma uchun g'alati bo'shliq.

---

## ⑦ Ma'lumot kiritish nomuvofiqligi

**Daraja:** past · **Turi:** ma'lumotlar sifati

Bir sinf ro'yxatida o'quvchilar ismlari **qisman lotin, qisman kirill**
alifbosida kiritilgan. Bu:

- Alifbo bo'yicha saralashni buzadi (lotin ismlar ro'yxat boshida,
  kirill ismlar oxirida to'planadi)
- Qidiruvni murakkablashtiradi
- Chop etilgan PIN kartochkalarida g'alati ko'rinadi

Yechim: import bosqichida transliteratsiya yoki normalizatsiya.

---

## ⑧ `safe-area-inset` ishlatilmagan

**Daraja:** past

iPhone'ning pastki "home indicator" zonasi hisobga olinmagan. Pastda
joylashgan elementlar (suzuvchi "Muammo haqida xabar bering" tugmasi)
shu zonaga tegib qolishi mumkin.

---

## ⑨ Print stillari juda kam

**Daraja:** past

Atigi 4 ta qoida: `print:hidden`, `print:block`, `print:flex`,
`print:hover:bg-transparent`.

Platformada **"PIN kartochkalarini chop etish"** funksiyasi borligini
hisobga olsak, bu juda kam. Chop etish ko'rinishi tekshirilmagan — ehtimol
alohida sahifa yoki komponent orqali qilingandir.

---

# Jonli darsda topilganlar (2026-09-25)

Haqiqiy dars kuzatuvidan — [08-jonli-dars.md](08-jonli-dars.md). Bu bo'lim
ham ichida muhimlik bo'yicha tartiblangan.

---

## ⑩ Dars oxirida o'qituvchi paneldan chiqarib yuboriladi

**Daraja:** yuqori · **Ta'sir:** har bir uzun jonli dars

Viktorina g'oliblari ekranidan keyin panel o'z-o'zidan `/login` ga o'tdi:

```
~08:52    kirish
09:44:12  oxirgi muvaffaqiyatli HTTP so'rov
          (keyingi 4 daqiqada monitor faqat WebSocket bilan ishladi)
09:48:43  /organizations/{id}/feedback            → 401
09:48:57  /me, /classes, /organizations/{id}/me   → 401 (×8)
09:48:59  → /login
```

`/auth/logout` chaqirilmagan, ya'ni o'qituvchi o'zi chiqmagan.

**Ehtimoliy sabab:** kirish tokeni taxminan 45 daqiqa amal qiladi. Jonli
dars paytida monitor HTTP so'rov yubormaydi (hammasi WebSocket orqali),
shuning uchun token yangilanmaydi. Dars oxirida birinchi HTTP so'rov 401
oladi va panel o'qituvchini chiqarib yuboradi. 45 daqiqalik dars uchun bu
**aynan dars oxiriga** to'g'ri keladi.

**Oqibat:**

- Dars oxiridagi `/feedback` so'rovi (o'qituvchi fikri yoki muammo xabari)
  401 bilan qaytgan — yo'qolgan bo'lishi mumkin
- O'qituvchi darsni yakunlash oqimini tugata olmaydi, qayta kirishi kerak.
  Dars yakunlanmay qolsa, natijalar oraliq holatda qoladi
  ([03-dars-oqimi.md](03-dars-oqimi.md) — "tugallanmagan dars")

**Yechim:** dars davomida tokenni fon rejimida yangilab turish yoki
401 olganda avval refresh qilib, so'rovni takrorlash.

> Kuzatuvchi ham cookie bilan bir necha GET so'rov yuborgan. Ular
> autentifikatsiya holatini o'zgartirmasligi kerak, lekin bu to'liq
> istisno qilinmagan. Tasdiqlash uchun kuzatuvchisiz 45+ daqiqalik darsda
> takrorlash kerak.

---

## ⑪ Suzuvchi tugma "Davom etish" ni to'sib qo'yadi

**Daraja:** o'rta · **Ta'sir:** tor ekranda monitor

~800px kenglikda o'ng pastdagi suzuvchi **"Muammo haqida xabar bering"**
tugmasi monitor pastki panelidagi **"Davom etish →"** tugmasining ustiga
tushadi — matn "Davon…" bo'lib kesiladi. Bu amaliyotdan keyingi qadamga
o'tadigan asosiy tugma. 1902px kenglikda muammo yo'q.

**Yechim:** monitor sahifasida suzuvchi tugmani yashirish yoki pastki panelga
o'ng tomondan joy (padding) qoldirish.

---

## ⑫ Podiumda uzun ism so'z o'rtasidan bo'linadi

**Daraja:** past · **Ta'sir:** proyektordagi viktorina yakuni

"Viktorina g'oliblari" podiumida to'liq F.I.Sh. (otasining ismi bilan,
katta harfda) ko'rsatiladi. Uzun ism ustunga sig'maydi va **so'z o'rtasidan**
bo'linadi — oxirgi harf alohida qatorga tushadi.

**Yechim:** podiumda faqat ism + familiya ko'rsatish (monitor chiplarida
allaqachon faqat familiya ishlatilgan), sig'magan so'zni esa bo'lmasdan
kichraytirish yoki qisqartirish.

---

## ⑬ Kontent so'rovlarida CORS xatolari

**Daraja:** past · **Turi:** texnik

`/api/v1/content/scenes/{sha256}` so'rovlari konsolda ~70 marta
*"No 'Access-Control-Allow-Origin' header"* xatosi bilan bloklangan
(16 sahnaning har biri 4–5 martadan). Slaydlar baribir ko'rindi — boshqa
urinish yoki kesh orqali bo'lsa kerak. Natija: ortiqcha trafik va
konsoldagi shovqin haqiqiy xatolarni yashiradi.

---

## Xulosa

Platforma texnik jihatdan puxta qurilgan: tizimli tokenlar, izchil
komponentlar, kuchli accessibility semantikasi, `prefers-reduced-motion`
qo'llab-quvvatlashi. Kamchiliklar asosan **ikki joyda to'plangan**:

1. **Rang tanlovi** — brend rangi chiroyli, lekin oq matn bilan o'qilmaydi
2. **Mobil responsive** — bitta grid to'liq e'tibordan chetda qolgan

Ikkalasi ham tuzatish oson — tizimning o'zi to'g'ri qurilgan.

Jonli dars kuzatuvi uchinchi, jiddiyroq joyni ko'rsatdi:
**sessiya muddati** (⑩). U darsning eng muhim lahzasida — yakunlashda —
o'qituvchini chiqarib yuboradi.
