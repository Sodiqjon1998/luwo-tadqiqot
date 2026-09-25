# 07 — Ochiq savollar va keyingi qadamlar

Tadqiqotda hali yopilmagan joylar. Ishxonada davom ettirish uchun ro'yxat.
Yopilgan savollar yonida qisqa javob va manba bor.

---

## 1. Jonli dars ekrani

2026-09-25 da haqiqiy dars davomida kuzatildi —
[08-jonli-dars.md](08-jonli-dars.md).

- [x] Kutish xonasi (lobby) qanday ko'rinadi? Hisoblagich qayerda?
      → "HALI KIRMADI / SINFDA" guruhlari, pastda "Ulandi: 16 tadan N tasi" (08 §2)
- [x] Monitor ekrani — yo'lakchalar (lane) qanday joylashgan?
      → Lane — **topshiriq** qatori, bolalar unda chip bo'lib turadi (08 §4)
- [ ] Qo'l ko'tarish (`hand`) — bola qanday so'raydi, o'qituvchi qanday ko'radi?
      → O'qituvchi tomoni: "Qo'llar ko'tarilgan" filtri, `acknowledge_hand`.
      Darsda hech kim qo'l ko'tarmadi; bola tomoni ko'rilmadi
- [x] "Chiqib ketgan" (`away`) holati qachon paydo bo'ladi? Ulanish uzilsami?
      → Ha, ulanish uzilganda: "Oflayn" filtri + "Tarmoqda yo'q" (Phoenix Presence)
- [x] `idle` (harakatsiz) — necha soniyadan keyin?
      → **2 daqiqa** bitta topshiriqda: "bitta ekranda N daq" (08 §4)
- [x] `mirror-pane` — o'qituvchi bolaning ekranini ko'ra oladimi?
      → Ha, har bola uchun "Sinfga ko'rsatish". Video emas, event oqimi (08 §9).
      UI ichi ko'rilmadi (tugma bosilmadi)
- [x] Slaydni oldinga surish o'qituvchidami yoki bola o'zi ketadimi?
      → O'qituvchida (miniatyuralar, strelkalar) (08 §3)
- [ ] Darsni yakunlash tugmasi qayerda, nima so'raydi?
      → Qayerda: sarlavhaning o'ng tomonida, ochiluvchi menyu bilan.
      Nima so'rashi ko'rilmadi — o'qituvchi majburan chiqarildi (06 ⑩)
- [x] Dark tema haqiqatan ishlatiladimi (`canvas #0f172a`)?
      → O'quvchi ilovasida ha. O'qituvchi monitori butun dars davomida yorug'

**Yangi savollar:**

- [ ] **O'yin maydoni** (3-qadam) ichida nima bor? Bolalar nima qiladi?
- [ ] "Diqqat" tugmasi bosilganda bolalar ekranida nima bo'ladi? Necha soniyaga?
- [ ] "Sessiyani bekor qilish" va `false_start_spent` — necha marta bekor qilish mumkin?
- [ ] `evict_student` — bolani chiqarish UI da qayerda?
- [ ] `LessonFinale` ekrani va darsni yakunlash oqimi
- [ ] Majburiy chiqish (06 ⑩) kuzatuvchisiz ham takrorlanadimi?

---

## 2. O'quvchi tomoni (`student.luwo.ai`)

Faqat kirish ekrani ko'rildi (08 §10).

- [ ] Kirish ekrani — kod, ism tanlash, PIN qanday ko'rinadi?
      → Kod ekrani ko'rildi (6/8 xonali, ekrandagi raqamli klaviatura).
      Ism tanlash va PIN — hali yo'q
- [x] "Dars" va "Uy vazifasi" bo'limlari farqi
      → "В классе" 6 xonali jonli kod, "Дома" 8 xonali o'zgarmas kod
- [ ] Mashq topshiriqlari qanday turdagi? (drag-drop, tanlov, kod yozish?)
      → Kod nomlaridan: brauzer ichidagi simulyatsiyalar (OS, Office, Word,
      Paint, Terminal, qidiruv, jadval, bloklar). Bola ekranida ko'rilmadi
- [ ] Block Studio (Scratch uslubidagi muhit) qanday ishlaydi?
- [ ] Bola xato qilsa nima bo'ladi — qayta urinish bormi?
      → Qayta urinish bor: monitorda "N urinish" (3 dan boshlab signal).
      Bolaga qanday ko'rinishi — noma'lum
- [ ] Interfeys 1-sinf bolasi uchun qanchalik soddalashtirilgan?

---

## 3. Mashq (amaliyot) tuzilishi

- [x] Topshiriqlar dars ichida qayerda joylashgan — slaydlar orasidami yoki oxiridami?
      → Taqdimotdan **keyin**, alohida qadam. Faqat oxirgi slayddan ochiladi (08 §1)
- [ ] "Ball" (≈43) qanday hisoblanadi? Topshiriq + viktorina o'rtachasimi?
      → Viktorina balli tezlikka bog'liq (08 §7). Natijalar jadvalidagi ≈43 — hali noma'lum
- [ ] Topshiriqlarni o'qituvchi qo'lda tekshirishi mumkinmi?
      → Tekshiruv avtomatik (validator kalitlari, 08 §9). Qo'lda tekshirish ko'rinmadi

---

## 4. Tekshirilmagan amallar

- [ ] **PIN kartochkalarini chop etish** — qanday ko'rinish chiqadi?
      (Print stillari juda kam edi — alohida sahifami?)
- [ ] **Boshqa sinfga o'tkazish** — qanday dialog, natijalar ko'chadimi?
- [ ] **Til almashtirish** — interfeys tilini o'zgartirish nimani o'zgartiradi?
      → Qisman: yangi brauzerda panel inglizcha, o'quvchi ilovasi ruscha ochildi.
      Ya'ni boshlang'ich til ikki ilovada har xil tanlanadi
- [ ] **Avatar o'zgartirish** — o'quvchi rasmini almashtirish oqimi
- [ ] **Parolni tiklash** (`/forgot-password`) oqimi
- [ ] **Murojaat yuborish** — yuborilgandan keyin nima bo'ladi, javob qayerda keladi?

---

## 5. Aniqlanishi kerak bo'lgan savollar

### Dars kodi haqida

- [x] Kod necha xonali? Uy kodi 8 xonali edi — dars kodi ham shundaymi?
      → Jonli dars kodi **6 xonali**
- [ ] Dars tugagach kod bekor bo'ladimi?
- [ ] Bir vaqtda ikki sinfda dars o'tkazish mumkinmi?
      → `/sessions/live` massiv qaytaradi — texnik jihatdan bir nechta bo'lishi mumkin
- [ ] Dars yarmida kirgan bola qayerdan boshlaydi?
      → Kirish mumkinligi tasdiqlandi (boshlash dialogi). Qayerdan boshlashi — noma'lum

### Modul 1 dagi 7-dars

- [ ] Nega `/curriculum` da 10 dars, sinf sahifasida 9 ta?
- [ ] 7-dars ("Ekrandan dam olish vaqti") boshqa sinflarda ham yo'qmi?
- [ ] Maktab darslarni o'chira oladimi (sozlama bormi)?

### Ko'nikmalar tizimi

- [ ] Ko'nikmalar ro'yxati qayerdan olinadi — standartlarga bog'langanmi?
- [ ] Bir dars nechta ko'nikma beradi?
- [ ] Ota-ona bu hisobotni ko'ra oladimi?

### Rollar

- [ ] O'qituvchidan tashqari boshqa rollar bormi (direktor, metodist)?
- [ ] Maktab administratori paneli bormi?
- [ ] "Keyingi marra" (10 dars) ko'rsatkichi nima — gamifikatsiyami?

---

## 6. Texnik savollar

- [x] API tuzilishi qanday? (Network so'rovlarini kuzatish kerak)
      → REST `api.luwo.ai/api/v1` + WebSocket `/socket` (08 §9)
- [x] Jonli dars real-time qanday ishlaydi — WebSocket, SSE yoki polling?
      → **WebSocket, Phoenix Channels** (Elixir), LongPoll zaxirasi bilan (08 §9)
- [ ] Offline rejim bormi? Internet uzilsa dars davom etadimi?
      → Mijozda qayta ulanish va LongPoll bor. Amalda sinalmadi
- [ ] Sessiya qancha vaqt saqlanadi?
      → Taxminan 45 daqiqa, keyin 401 va chiqarib yuborish (06 ⑩). Tasdiqlash kerak
- [ ] `beyond_coding` — tayyorgarlik oynasi pastidagi bu belgi nima?
      (Build nomi? Kompaniyaning ichki nomi?)

---

## Keyingi seans uchun tavsiya

1. **Majburiy chiqishni tasdiqlash** (06 ⑩) — kuzatuvchisiz, 45 daqiqadan
   uzoqroq darsda. Tasdiqlansa, Luwo'ga birinchi navbatda yuboriladigan xabar shu.
2. **O'quvchi tomoni** — test o'quvchi bilan (inkognito oynada) bitta
   darsni boshdan-oxir o'tish: ism tanlash, PIN, mashq ichi, qo'l ko'tarish,
   O'yin maydoni.
3. **Dars yakuni** — "Darsni yakunlash" dialogi va `LessonFinale` ekrani.
