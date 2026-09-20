# Video-chat signaling server — o'rnatish yo'riqnomasi

Bu server o'zi video ko'rsatmaydi — u faqat ikki telefonni bir-biriga
"ulaydi" (kim kimga qo'ng'iroq qilyapti, degan xabarlarni uzatadi).
Video/ovoz oqimining o'zi keyin to'g'ridan-to'g'ri ikki telefon
o'rtasida (yoki TURN server orqali) o'tadi.

## 1-qadam — kompyuteringizda sinab ko'rish (ixtiyoriy, lekin tavsiya etiladi)

1. [nodejs.org](https://nodejs.org) dan Node.js ni o'rnating (LTS versiya).
2. Shu papkani (`signaling-server`) kompyuteringizga tushiring.
3. Terminalda shu papka ichida:
   ```
   npm install
   npm start
   ```
4. `Signaling server 3000-portda ishga tushdi` deb yozsa — ishlayapti.

## 2-qadam — internetga chiqarish (Render.com — bepul)

Telefoningizdagi ilova serverga ulanishi uchun, server internetda
doim ishlab turishi kerak. Eng oson bepul yo'l — Render.com:

1. [render.com](https://render.com) da ro'yxatdan o'ting (GitHub akkaunt bilan kirsa bo'ladi).
2. GitHub'da yangi repository oching va shu `signaling-server` papkasidagi
   3 ta faylni (`server.js`, `package.json`, `README.md`) shu repo'ga yuklang.
3. Render'da: **New + → Web Service** → GitHub repo'ingizni tanlang.
4. Sozlamalar:
   - **Build Command:** `npm install`
   - **Start Command:** `npm start`
   - **Instance Type:** Free
5. "Create Web Service" bosing. Bir necha daqiqadan so'ng sizga
   shunga o'xshash manzil beriladi:
   `https://sizning-ilovangiz.onrender.com`
6. WebSocket manzilingiz shu bo'ladi (https → wss ga almashtiring):
   `wss://sizning-ilovangiz.onrender.com`

   Shu manzilni menga bersangiz, ilovadagi video-chat kodini
   shu serverga ulaydigan qilib yozib beraman.

⚠️ Eslatma: Render bepul tarifda server 15 daqiqa ishlatilmasa "uxlab qoladi"
va keyingi qo'ng'iroqda 30–60 soniya sekin ochiladi. Doimiy tezlik uchun
pullik tarif ($7/oy dan) kerak bo'ladi.

## 3-qadam — TURN server (muhim!)

Ikki telefon turli tarmoqda (masalan biri Wi-Fi, biri mobil internet)
bo'lsa, ko'pincha to'g'ridan-to'g'ri ulanish ishlamaydi — TURN server
kerak bo'ladi. O'zingiz TURN server qurish murakkab, shuning uchun
tayyor bepul/arzon xizmatdan foydalanish tavsiya etiladi:

- [metered.ca/tools/openrelay](https://www.metered.ca/tools/openrelay/) — bepul, ro'yxatdan o'tib API kalit olasiz
- yoki Twilio, Xirsys kabi xizmatlar (oz pullik, ishonchliroq)

TURN ma'lumotlarini (server manzili, username, parol) olganingizdan
so'ng ham menga bering — ilova kodiga qo'shib beraman.

## Xulosa — nima kerak bo'ladi

| Qadam | Nima qilasiz | Narxi |
|---|---|---|
| 1 | Render.com'da serverni joylashtirasiz | Bepul |
| 2 | Metered.ca'dan TURN kalit olasiz | Bepul (limit bilan) |
| 3 | Ikkalasining manzilini menga berasiz | — |
| 4 | Men ilovani shu serverlarga ulaydigan qilib yozib beraman | — |
