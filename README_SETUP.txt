MODZ WEB PRO - SETUP

1) ارفع indexx.html إلى الاستضافة أو Firebase Hosting.
2) في Firebase Console > Firestore > Rules ضع محتوى firestore.rules ثم Publish.
3) لا تحتاج Firebase Storage أو Storage Rules لهذه النسخة.
4) نظام الإدارة:
   - تسجيل الدخول العادي يتم من نفس حساب Firebase Authentication.
   - زر الإدارة يطلب رقم المطور 01103286334 وكلمة المرور 12347890.
   - بعد نجاح بيانات الإدارة، يجب أن يكون UID للحساب الحالي موجودًا في:
       admins/{UID}
     ويحتوي مثلًا:
       enabled: true
       role: "admin"
   - أنشئ هذا المستند يدويًا مرة واحدة من Firestore Console لحساب المدير.
5) زر المطور:
   - اتصال: 01103286334
   - واتساب: 201103286334

مهم جدًا:
كلمة مرور لوحة الإدارة المكتوبة داخل HTML ليست سرًا حقيقيًا؛ أي شخص يستطيع فحص JavaScript. لذلك صلاحيات Firebase الفعلية لا تعتمد على كلمة المرور الموجودة في الصفحة، بل على admins/{UID} وقواعد Firestore. هذا يمنع المستخدم العادي من الحصول على صلاحيات المدير بمجرد معرفة كلمة المرور.

صلاحيات الإدارة داخل الواجهة:
- حظر المستخدم/فك الحظر.
- تعديل الرتبة user / moderator / admin.
- حذف ملف المستخدم من Firestore.
- متابعة المستخدمين.

الحظر يمنع التطبيق من الاستمرار للمستخدم عند دخوله، لكنه لا يحذف حساب Firebase Authentication نفسه. حذف حساب Auth فعليًا يحتاج Firebase Admin SDK/Cloud Function أو حذفًا يدويًا من Authentication.
