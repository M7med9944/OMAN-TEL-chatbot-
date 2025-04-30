# OMAN-TEL-chatbot-

# مشروع: مساعد عمانتل الذكي

## 1. تشكيل فريق Scrum
|الدور|الاسم (Placeholder)|المسؤوليات|
|-----|-------------------|-------------|
|Product Owner|[اسم مسؤول عمانتل]|تحديد الأولويات، التواصل مع stakeholders|
|Scrum Master|[اسم Scrum Master]|إدارة الاجتماعات، إزالة العقبات، ضمان تطبيق Agile|
|Backend Engineer|[اسم]|تصميم وبناء API، تكامل مع أنظمة عمانتل|
|Frontend Engineer|[اسم]|تطوير واجهة المستخدم (ويب/واتساب)
|ML Engineer|[اسم]|بناء ونشر نموذج NLP/ML
|DevOps Engineer|[اسم]|إعداد CI/CD، البنية التحتية، الأمان

> **Action**: استكمل أسماء الفريق في الجدول أعلاه.

---

## 2. إعداد الأدوات
1. **GitHub Repository**
   - أنشئ repo باسم `omantel-ai-assistant`
   - أضف README.md (هذا الملف)
2. **Jira Project**
   - أنشئ مشروع Scrum باسم `Omantel-AI`
   - أضف Epics: `Authentication`, `Billing Queries`, `Package Renewal`, `Outage Reporting`, `NLP Engine`
3. **CI/CD**
   - GitHub Actions: ملف `.github/workflows/ci.yml`
   - إعداد اختبارات تلقائية و linting
4. **Gemini API**
   - سجل للحصول على API Key من منصة Gemini
   - احفظ المفتاح في GitHub Secrets باسم `GEMINI_API_KEY`
5. **بيئة التطوير المحلية**
   - أنشئ ملف `.env` يحتوي على:
     ```ini
     GEMINI_API_KEY=your_api_key_here
     OMANTEL_API_URL=https://api.omantel.local
     ```

> **Action**: أكمل كل إعداد وخطّط لتأكيد الوصول إلى المفاتيح قبل بدء الترميز.

---

## 3. أولى المهام (Sprint 0)
1. إعداد الهيكلية الأساسية للمشروع:
   - مجلدات: `backend/`, `frontend/`, `ml/`, `infra/`
   - ملفات تهيئة: `docker-compose.yml`, `requirements.txt`, `package.json`
2. تصميم معماري عالي المستوى:
   - ارسم مخطط يوضح تدفق البيانات بين المستخدم، الواجهة، خدمة الـ NLP، وأنظمة عمانتل.
3. تأكد من إمكانية الاتصال بGemini API بنموذج اختبار بسيط:
   - سكربت Python يرسل استعلام تجريبي ويطبع الاستجابة.

> **Action**: نفّذ المهمة 3 الآن: أنشئ سكربت في `ml/test_gemini.py` وجرب الاتصال.

---

## 4. الخطوة التالية بعد الانتهاء
- راجع نتائج الاتصال بالـ Gemini API.
- جهّز أول User Story في Jira: "كمستخدم، أريد أن أسأل عن قيمة فاتورتي، فيتصل الـ Bot بالـ API ويعيد الرقم".
- اختر Sprint 1 وابدأ التخطيط.

> **Action**: عقب تنفيذ سكربت الاتصال، اعمل تعليق هنا بنتيجة الاختبار لنمضي إلى تخطيط Sprint 1.
