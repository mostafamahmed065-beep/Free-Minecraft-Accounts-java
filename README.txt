MC ACCOUNTS — الموقع + السيرفر (ملف واحد يرفع كله)
====================================================

STRUCTURE:
  server.js          ← السيرفر (Express)
  package.json
  public/index.html  ← الموقع نفسه (واجهة المتابعين + لوحة الأدمن)
  data.json          ← بيتعمله تلقائياً (الحسابات + عدد المسحوب)

RUN LOCALLY:
  npm install
  ADMIN_PASS=M0st@f@_Pr0 npm start
  http://localhost:3000

DEPLOY — Render.com (الأسهل):
  1) ارفع الفولدر ده على GitHub (repo جديد).
  2) Render → New → Web Service → اختار الـ repo.
     Build: npm install      Start: npm start
  3) Environment → Add:
        ADMIN_PASS = M0st@f@_Pr0
        DATA_DIR   = /var/data
  4) Advanced → Add Disk:  Name=data  Mount Path=/var/data  Size=1GB
     (لو مش هتعمل Disk، البيانات هتضيع مع كل Restart)
  5) Deploy → هتاخد لينك زي https://xxx.onrender.com — ده لينك الموقع اللي تبعته للمتابعين.

ALTERNATIVE — Railway: نفس الخطوات، Railway بيدي Volume تلقائي.

NOTES:
  - الكولداون 7 دقايق لكل IP (محفوظ في السيرفر).
  - لوحة الأدمن: زر ⚙️ → باسورد → لصق الحسابات → Save (بيضيف فوق الموجود)
    أو Replace All (يمسح كل حاجة ويبدأ من جديد).
  - الموقع والسيرفر على نفس الدومين، فمش محتاج تعمل أي إعداد في الواجهة.
  - لو رفعت الواجهة لوحدها على دومين تاني: افتح index.html وحط رابط السيرفر في SERVER_URL.
