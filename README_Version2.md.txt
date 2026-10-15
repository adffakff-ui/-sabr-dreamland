# استراحة صبر دريم لاند

تطبيق ويب بسيط (واجهة + خادم Node/Express) لاستقبال طلبات الحجز والرسائل مع لوحة إدارة محمية.

تشغيل محلي:
1. انسخ المشروع إلى جهازك (كما في هيكل الملفات).
2. ثبت الاعتمادات:
   npm install
3. اضبط متغيرات البيئة (مهم للحماية والإشعارات):
   - ADMIN_USER (مثال: admin)
   - ADMIN_PASS (مثال: strongPassword)
   - SESSION_SECRET (سلسلة عشوائية)
   - (اختياري) ADMIN_BASIC_ENABLE=true
   - (اختياري إذا فعّلت) ADMIN_BASIC_USER و ADMIN_BASIC_PASS
   - (اختياري لإشعارات البريد) SMTP_HOST, SMTP_PORT, SMTP_USER, SMTP_PASS, EMAIL_TO
4. شغل التطبيق:
   npm start
5. افتح المتصفح:
   - الموقع: http://localhost:3000
   - لوحة الإدارة: http://localhost:3000/admin/login

تشغيل عبر Docker:
1. بناء الصورة:
   docker build -t sabrdreamland .
2. تشغيل الحاوية (مثال مع متغيرات env):
   docker run -p 3000:3000 -e ADMIN_USER=admin -e ADMIN_PASS=yourPass -e SESSION_SECRET=mysecret sabrdreamland

ملاحظات أمنية:
- Basic Auth يحمِي مسارات الإدارة عند تفعيله (ضع ADMIN_BASIC_ENABLE=true مع ADMIN_BASIC_USER و ADMIN_BASIC_PASS).
- في بيئة الإنتاج استخدم HTTPS وReverse Proxy (Nginx) واحفظ الجلسات في Redis.
- البيانات تحفظ محليًا في مجلد data/ (bookings.json و contacts.json). لبيئة إنتاج استخدم قاعدة بيانات.
