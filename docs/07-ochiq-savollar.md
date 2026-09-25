# 07 — Ochiq savollar va keyingi qadamlar

Tadqiqotda hali yopilmagan joylar. Ishxonada davom ettirish uchun ro'yxat.

---

## 1. Jonli dars ekrani — eng muhim bo'shliq

Hech qachon ochilmagan (dars boshlash o'quvchilar ekraniga chiqadi va
yozuv qoldiradi). Kod tahlilidan nimalar borligi ma'lum, lekin qanday
ko'rinishi noma'lum.

**Tekshirish kerak:**

- [ ] Kutish xonasi (lobby) qanday ko'rinadi? Hisoblagich qayerda?
- [ ] Monitor ekrani — yo'lakchalar (lane) qanday joylashgan?
- [ ] Qo'l ko'tarish (`hand`) — bola qanday so'raydi, o'qituvchi qanday ko'radi?
- [ ] "Chiqib ketgan" (`away`) holati qachon paydo bo'ladi? Ulanish uzilsami?
- [ ] `idle` (harakatsiz) — necha soniyadan keyin?
- [ ] `mirror-pane` — o'qituvchi bolaning ekranini ko'ra oladimi?
- [ ] Slaydni oldinga surish o'qituvchidami yoki bola o'zi ketadimi?
- [ ] Darsni yakunlash tugmasi qayerda, nima so'raydi?
- [ ] Dark tema haqiqatan ishlatiladimi (`canvas #0f172a`)?

> ⚠️ Buni sinash uchun haqiqiy sinf kerak emas — bo'sh sinfda ham dars
> boshlab ko'rish mumkin, lekin yozuv qoladi. Test sinfi bo'lsa yaxshi.

---

## 2. O'quvchi tomoni (`student.luwo.ai`)

Umuman ochilmagan.

- [ ] Kirish ekrani — kod, ism tanlash, PIN qanday ko'rinadi?
- [ ] "Dars" va "Uy vazifasi" bo'limlari farqi
- [ ] Mashq topshiriqlari qanday turdagi? (drag-drop, tanlov, kod yozish?)
- [ ] Block Studio (Scratch uslubidagi muhit) qanday ishlaydi?
- [ ] Bola xato qilsa nima bo'ladi — qayta urinish bormi?
- [ ] Interfeys 1-sinf bolasi uchun qanchalik soddalashtirilgan?

---

## 3. Mashq (amaliyot) tuzilishi

Natijalarda "7 tadan 3 ta" ko'rinadi, lekin topshiriqlarning o'zi
o'qituvchi tomonidan ko'rinmaydi.

- [ ] Topshiriqlar dars ichida qayerda joylashgan — slaydlar orasidami yoki oxiridami?
- [ ] "Ball" (≈43) qanday hisoblanadi? Topshiriq + viktorina o'rtachasimi?
- [ ] Topshiriqlarni o'qituvchi qo'lda tekshirishi mumkinmi?

---

## 4. Tekshirilmagan amallar

- [ ] **PIN kartochkalarini chop etish** — qanday ko'rinish chiqadi?
      (Print stillari juda kam edi — alohida sahifami?)
- [ ] **Boshqa sinfga o'tkazish** — qanday dialog, natijalar ko'chadimi?
- [ ] **Til almashtirish** — interfeys tilini o'zgartirish nimani o'zgartiradi?
- [ ] **Avatar o'zgartirish** — o'quvchi rasmini almashtirish oqimi
- [ ] **Parolni tiklash** (`/forgot-password`) oqimi
- [ ] **Murojaat yuborish** — yuborilgandan keyin nima bo'ladi, javob qayerda keladi?

---

## 5. Aniqlanishi kerak bo'lgan savollar

### Dars kodi haqida

- [ ] Kod necha xonali? Uy kodi 8 xonali edi — dars kodi ham shundaymi?
- [ ] Dars tugagach kod bekor bo'ladimi?
- [ ] Bir vaqtda ikki sinfda dars o'tkazish mumkinmi?
- [ ] Dars yarmida kirgan bola qayerdan boshlaydi?

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

- [ ] API tuzilishi qanday? (Network so'rovlarini kuzatish kerak)
- [ ] Jonli dars real-time qanday ishlaydi — WebSocket, SSE yoki polling?
- [ ] Offline rejim bormi? Internet uzilsa dars davom etadimi?
- [ ] Sessiya qancha vaqt saqlanadi?
- [ ] `beyond_coding` — tayyorgarlik oynasi pastidagi bu belgi nima?
      (Build nomi? Kompaniyaning ichki nomi?)

---

## Keyingi seans uchun tavsiya

Eng katta qiymat **jonli dars ekranida**. Butun platformaning mag'zi shu yerda,
va aynan u hali ochilmagan. Agar test sinfi yoki bo'sh sinf bo'lsa, bitta
darsni boshdan-oxir o'tkazib ko'rish — qolgan barcha savollarning yarmiga
javob beradi.

Ikkinchi o'rinda — `student.luwo.ai`, chunki mashq topshiriqlarining
haqiqiy tuzilishi faqat o'sha yerda ko'rinadi.
