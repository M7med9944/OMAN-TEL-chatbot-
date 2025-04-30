# مشروع: مساعد عمانتل الذكي (نسخة أولية خفيفة)

## ملاحظات أساسية
- **ليس هناك وصول مباشر لبيانات عمانتل**، سنستخدم بيانات تجريبية تُجمع يدويًا (أسئلة وأجوبة شائعة).
- نبدأ بـ **نسخة خفيفة (PoC)** قابلة للتطوير لاحقًا عند توفر البيانات الحقيقية.
- سنستخدم **Gemini API** لتوليد ردود مبنية على نموذج لغة عام، مع ضبط بسيط على الأسئلة المتكررة.

---

## 1. تشكيل فريق مصغر (PoC Team)
|الدور|الاسم (Placeholder)|المسؤوليات|
|-----|-------------------|-------------|
|Project Lead|[اسمك]|تنسيق العمل، جمع الأسئلة يدويًا، اختبار النموذج|
|ML/AI Engineer|[اسم]|إعداد واختبار Gemini API، ضبط الـ prompts|
|Frontend Engineer|[اسم]|واجهة بسيطة لاختبار المحادثة (ويب أو CLI)|

> **Action**: أكمل أسماء الفريق.

---

## 2. إعداد PoC بدون بيانات حقيقية
1. **بيانات تجريبية**
   - اجمع يدويًا **20 سؤالاً وإجاباتها** حول الفواتير، تجديد الباقات، الأعطال.
   - احفظها في ملف JSON: `ml/sample_faq.json`:
     ```json
     [
       {"question": "كم قيمة فاتورتي؟", "answer": "قيمة فاتورتك هي 10 ريالات عمانية."},
       ...
     ]
     ```
2. **سكربت اختبار بسيط** (`ml/test_gemini.py`):
   - يحمّل `sample_faq.json`
   - يستقبل سؤال من المستخدم
   - يبحث تطابقًا دقيقًا أو جزئيًا في الأسئلة التجريبية
   - إذا لم يجد، يرسل السؤال إلى Gemini API مع prompt:  
     `"Answer as Omantel support: <user_question>"`
   - يعرض الإجابة
3. **تشغيل محلي**
   - `python ml/test_gemini.py`
   - جرب أسئلة من القائمة وأسئلة جديدة

> **Action**: جهّز `sample_faq.json` وملف `test_gemini.py` ونفّذ اختبارًا أوليًا.

---

## 3. مثال كود للـ PoC
```python
import json
import os
from gemini import GeminiClient  # افترض وجود مكتبة عميلة

# تحميل الأسئلة التجريبية
def load_faq(path="ml/sample_faq.json"): 
    return json.load(open(path, 'r', encoding='utf-8'))

# إعداد عميل Gemini
client = GeminiClient(api_key=os.getenv("GEMINI_API_KEY"))

faq = load_faq()

# دالة للإجابة

def get_answer(question):
    # البحث في الأسئلة التجريبية
    for item in faq:
        if item['question'] in question:
            return item['answer']
    # طلب من Gemini
    prompt = f"Answer as Omantel support to this customer query in Arabic: {question}"
    resp = client.generate(prompt)
    return resp.text

if __name__ == '__main__':
    while True:
        q = input("سؤال العميل: ")
        if q.lower() in ('exit', 'quit'):
            break
        print("المساعد: ", get_answer(q))
```

---

## 4. الخطوة التالية بعد PoC
- وثّق ملاحظات الأداء: دقة الإجابات من الـ FAQ مقابل Gemini.
- حدّد احتياجات البيانات الحقيقية: أنواع الأسئلة، حجم الأنماط.
- بعد جمع بيانات كافية، ننتقل إلى خطة Agile موسعة وتكامل آمن.

> **Action**: نفّذ PoC الآن وشارك النتائج (مثال سؤال وإجابة) لننتقل للمرحلة التالية.
