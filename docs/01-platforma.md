# 01 — Platforma haqida

## Nima bu

LUWO — xususiy maktablarning **1–8-sinflari uchun tayyor informatika o'quv
platformasi**. Pozitsiyalash shiori: *"Не курс программирования. С нами дети
учатся думать"* — ya'ni dasturlash kursi emas, balki tafakkur maktabi.

Asosiy va'da: o'qituvchi materialni noldan tayyorlamaydi — tayyor dars
stsenariysi, taqdimot, amaliyot va avtomatik tekshiruv platformada beriladi.

## Ko'lami

| Ko'rsatkich | Qiymat |
|---|---|
| Maktablar | 40+ |
| O'quvchilar | 14 000+ |
| Hozirgi mintaqa | Markaziy Osiyo |
| Keyingi mintaqalar | MENA/Gulf va Janubiy-Sharqiy Osiyo (2026–2027 reja) |

Marketing saytida hamkor maktablar ro'yxati keltirilgan: Tesla Academy,
Bilimkana American, Discovery School, Genius.KG, Arhimed School,
Avenir International School, Tensai va boshqalar — asosan Qirg'iziston va
O'zbekiston xususiy maktablari.

## Da'vo qilingan standartlar

Platforma 15 ta xalqaro ta'lim standartiga moslikni da'vo qiladi:

| Standart | Mintaqa | Da'vo |
|---|---|---|
| CSTA K-12 Computer Science | USA | Ko'rsatkichlardan oshadi |
| ISTE Standards | USA / Global | Ko'rsatkichlardan oshadi |
| Common Sense Education | USA, Digital Citizenship | Aksariyat ko'rsatkichlarda 10/10 |
| UK National Curriculum: Computing | UK KS1-3 | Asosiy bosqichlarda oshadi |
| Cambridge Primary & Lower Secondary | UK KS1-3 | 4 bosqichda to'liq moslik |
| UK DfE Education for a Connected World | UK / OFSTED | KS2 va KS3 oxirida 10/10 |
| GCSE/IGCSE Computer Science | UK / Xalqaro | Spetsifikatsiyaning 85–90% i 9-sinfga |
| IB PYP ICT + MYP Design | IB | Ikki dasturga mos |
| EU DigComp 2.2 | Yevropa Ittifoqi | Ko'rsatkichlardan oshadi |
| Singapore MOE Computing + Cyber Wellness | Singapur | Cyber Wellness bo'yicha 10/10 |
| ACARA Digital Technologies | Avstraliya | Ko'rsatkichlardan oshadi |
| UNESCO Media & Information Literacy | Xalqaro | To'liq mos |
| ABEGS Gulf Curriculum | MEA / GCC | Ko'rsatkichlarga mos |

> Bu da'volar marketing sahifasidan olingan va mustaqil tekshirilmagan.

## Metodika

Marketing sayti metodikani shunday tasvirlaydi:

```
VOPROS  →  LOGIKA  →  ALGORITM  →  RESHENIE
(savol)    (mantiq)    (algoritm)    (yechim)
```

**Spiral mikro-o'qitish:** qisqa qadamlar, amaliyot darhol, har bir ko'nikma
1-sinfdan 8-sinfgacha tobora chuqurroq qaytariladi.

O'qituvchi haqidagi pozitsiya: *"Мы не заменяем учителя — мы его усиливаем"* —
o'qituvchini almashtirmaymiz, kuchaytiramiz. Uchta va'da:

1. Tayyor dars strukturasi — o'qituvchi sinfni boshqaradi, material tayyorlamaydi
2. Butun sinfni onlayn ko'radi — kim ulgurmayotgani darhol ekranda
3. Avtomatik tekshirish va analitika — rutina kam, bolalarga e'tibor ko'p

## Uch qismli tuzilishi

| Qism | Manzil | Kim uchun |
|---|---|---|
| O'qituvchi paneli | `teacher.luwo.ai` | O'qituvchi: dars o'tkazish, sinf boshqaruvi, analitika |
| O'quvchi ilovasi | `student.luwo.ai` | Bolalar: darsga qo'shilish va uy vazifasi |
| Marketing sayti | `luwo.ai` | Maktab rahbariyati: demo so'rash |

O'qituvchi paneli — **SPA** (Single Page Application), React asosida,
Vite bilan yig'ilgan. Barcha kontent autentifikatsiyadan keyin ochiladi;
ochiq qismi faqat kirish sahifasi va parolni tiklash.

## Interfeys tillari

Platforma kamida uch tilni qo'llab-quvvatlaydi: **o'zbek**, **rus** va
(marketing saytida) **ingliz**. Muhim nozik jihat — **interfeys tili va sinf
tili alohida sozlanadi**: o'qituvchi panelni o'zbekcha ishlatib, rus tilidagi
sinfga dars bera oladi. Bolalar kontentni sinf tilida ko'radi.

Shriftlar ham shunga mos: latin, latin-ext, **kirill** va vetnam subsetlari
yuklangan.
