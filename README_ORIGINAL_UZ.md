# YUMI COIN — Telegram Mini App (Android uchun)

Bu loyiha Telegram Android ilovasi ichida ochiladigan Mini App va unga ulangan bot uchun boshlang‘ich, ishlaydigan loyiha.

## Hozir nimalar bor?
- Chiroyli, mobilga mos YUMI COIN interfeysi.
- Tangani bosib yig‘ish (oddiy o‘yinchi: har bosishda +1 coin va -1 energiya).
- Energiya vaqt o‘tishi bilan tiklanadi.
- Kunlik mukofot: 500 coin / 24 soat.
- Reyting jadvali va SQLite ma’lumotlar bazasi.
- `/start` bot buyrug‘i va Mini App tugmasi.
- Serverda tekshiriladigan Telegram `initData`.
- `ADMIN_TELEGRAM_ID` bilan belgilangan yagona admin uchun cheksiz coin va energiya; admin oddiy balansni o‘zgartira olmaydigan qilib klientga ishonib qolmaydi.

## Muhim: adminni xavfsiz sozlash
Admin ID — Telegram’ning raqamli foydalanuvchi IDsi. Uni kod ichiga hammaga ko‘rinadigan joyga yozmang; `.env` faylida saqlang. Faqat o‘zingizning ID raqamingizni kiriting. Bot tokenni hech kimga yubormang va GitHub’ga `.env` faylini yuklamang.

## Ishga tushirish
1. Telegram’da `@BotFather` ni oching, `/newbot` yuboring va bot yarating. Tokenni oling.
2. Loyihani Node.js qo‘llaydigan HTTPS hostingga joylang (masalan, Render kabi servis). Telegram Mini App uchun ommaviy HTTPS URL kerak.
3. Loyihada `.env.example` faylidan `.env` yarating va quyidagilarni to‘ldiring:
   - `BOT_TOKEN` — BotFather bergan token
   - `ADMIN_TELEGRAM_ID` — o‘zingizning raqamli Telegram ID’ingiz
   - `WEBAPP_URL` — deploy qilingan saytning `https://...` manzili
4. Terminalda `npm install`, keyin `npm start` ishga tushiring.
5. Botga `/start` yuboring va `🪙 YUMI COIN o‘ynash` tugmasini bosing.

## Android haqida
Bu Telegram ichida ishlaydigan Mini App; alohida APK shart emas. Android telefonda Telegram orqali ochiladi. Hostingga joylamasdan, faqat ZIP faylning o‘zi botni internetga chiqarmaydi. Alohida APK kerak bo‘lsa, keyin WebView wrapper yaratish mumkin, lekin Telegram botning serveri baribir internetda ishlashi kerak.

## Eslatma
- Bu starter loyiha. Real pul, kripto token, pul yechish/depozit funksiyalari yo‘q.
- SQLite fayli (`yumi.sqlite`) doimiy diskka ega hostingda saqlanishi kerak. Ephemeral hostingda ma’lumotlar yo‘qolishi mumkin; production uchun persistent disk yoki boshqariladigan database tanlang.
- Adminning “cheksiz” balansi interfeysda `∞` ko‘rinadi. Admin tap bosishlari statistika uchun sanaladi, oddiy o‘yinchilarning balansiga coin qo‘shilmaydi.
- O‘yinchi yuborgan oddiy JSON orqali admin maqomini soxtalashtirib bo‘lmaydi: server Telegram imzosini tekshiradi va admin IDni server konfiguratsiyasidan oladi.
