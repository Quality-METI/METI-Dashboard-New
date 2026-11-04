METI DASHBOARD — NEW SEPARATE GITHUB PAGES SITE
================================================

الهدف
-----
إنشاء موقع جديد منفصل عن الموقع الحالي، مع الاحتفاظ بالموقع القديم كما هو.
الواجهة مبنية على تصميم METI Dashboard المرجعي.

محتويات المجلد
--------------
index.html  : واجهة الموقع.
config.js   : مكان رابط Apps Script Backend الجديد بعد نشره.

تنبيه الحالة
------------
هذه حزمة Frontend مستقلة جاهزة للرفع على GitHub Pages.
ليست متصلة ببيانات الإنتاج بعد. APPS_SCRIPT_URL فارغ عمداً إلى أن يتم تجهيز
ونشر Backend الجديد واختبار دواله. لا تضع أي Supabase service_role key أو أسرار
في config.js أو index.html.

إنشاء Repository جديد
---------------------
1) افتح https://github.com/new
2) Repository name: METI-Dashboard-New
3) اختر Public (أو Private إذا كانت سياسة حسابك تسمح بـ GitHub Pages للخطة المستخدمة).
4) لا تختار Add README لأن الملف موجود في الحزمة.
5) اضغط Create repository.

رفع الملفات
-----------
1) افتح الـ Repository الجديد.
2) Add file > Upload files.
3) فك ضغط الحزمة وارفع index.html و config.js من داخل المجلد مباشرة إلى جذر الـ repo.
   مهم: لا ترفع المجلد الأب بحيث تصبح الملفات داخل مجلد فرعي.
4) Commit changes.

تفعيل GitHub Pages
------------------
1) Settings > Pages.
2) Build and deployment: Deploy from a branch.
3) Branch: main، Folder: / (root).
4) Save وانتظر اكتمال النشر.
5) الرابط سيكون غالباً:
   https://YOUR-GITHUB-USERNAME.github.io/METI-Dashboard-New/

ربط الـ Backend لاحقاً
----------------------
بعد نشر Backend Apps Script الجديد كـ Web App واختبار الـ /exec URL:
1) افتح config.js في GitHub.
2) Edit.
3) ضع رابط /exec في APPS_SCRIPT_URL بين علامتي الاقتباس.
4) Commit changes.
5) افتح الموقع الجديد واعمل Ctrl+Shift+R.

الـ Backend المطلوب
-------------------
الواجهة القديمة تعتمد على عدة RPC functions مثل login و getStats و getHomeBundle
و getQtcStats و getAttendance وغيرها. لا يكفي نشر Attendance module وحده لتشغيل
كل صفحات الداشبورد. يجب تجهيز Backend جديد يؤمن كل RPC المطلوبة ويتحقق من الدور
على السيرفر. الواجهة وحدها ليست نظام صلاحيات.

النطاق المتفق عليه
------------------
Home, Details of Data, Top Labelers, Top QTC, QTC Stats، و Admin > Attendance فقط.
لا تضف Details of Attendance أو Details of OT أو WLA أو Users.

مصادر البيانات
--------------
- Tasks: جدول Supabase الحالي public.meti_tasks (بدون إنشاء جدول Tasks مكرر).
- Attendance: Google Sheet ID:
  1hrSKe8eyvKruzEJ7Sdr5lrJl2XZoAwtwUI88GjyYojE
  Night tab GID: 69518175
- Timezone: Africa/Cairo

حافظ على الموقع القديم والـ Repository القديم دون أي تعديل.
