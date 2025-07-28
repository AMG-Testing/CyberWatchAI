📘 CyberWatch AI — دليل التشغيل

📌 مقدمة

CyberWatch AI هو وكيل ذكي لمراقبة النظام (عمليات، ملفات، شبكة) باستخدام Python، مع تدريب نموذج ذكاء اصطناعي لاكتشاف السلوكيات المشبوهة وتنبيه المستخدم عبر Telegram.


---

📋 المتطلبات

قبل البدء، تأكد من توفر:

Python 3.10+ مثبت على جهازك

Git (اختياري إذا ستنزل من GitHub مباشرة)

اتصال إنترنت لإعداد Telegram bot

صلاحية الوصول لتشغيل Python على جهازك



---

⚙️ تثبيت المشروع

1️⃣ تنزيل المشروع

يمكنك تنزيل المشروع كـ ZIP من GitHub.

اضغط Code → Download ZIP

فك الضغط في أي مكان على جهازك



---

2️⃣ إنشاء بيئة افتراضية

افتح PowerShell أو CMD داخل مجلد المشروع:

cd CyberWatchAI

python -m venv venv

.\venv\Scripts\activate


---

3️⃣ تثبيت المكتبات

بعد تفعيل البيئة الافتراضية:

pip install -r requirements.txt


---

🤖 إعداد Telegram Bot

1. افتح تطبيق Telegram


2. ابحث عن BotFather


3. ارسل الأمر:

/newbot


4. اتبع التعليمات للحصول على Bot Token


5. احصل على Chat ID الخاص بك عبر البوت @userinfobot


6. أنشئ ملف telegram_config.json داخل مجلد notifier:



{
  "BOT_TOKEN": "ضع التوكن هنا",
  "CHAT_ID": "ضع الشات آي دي هنا"
}


---

📊 جمع البيانات

قبل تدريب النموذج، تحتاج لتجميع بيانات نشاط النظام:

تشغيل وحدات المراقبة

افتح ثلاثة نوافذ PowerShell لتشغيل كل وحدة:

cd monitor

python process_monitor.py

cd monitor

python file_monitor.py

cd monitor

python network_monitor.py

💡 اتركها تعمل لفترة (مثلاً 30–60 دقيقة) لجمع بيانات كافية داخل مجلد data/.


---

🧠 تدريب نموذج الذكاء الاصطناعي

بعد جمع البيانات:

cd model

python train_model.py

💡 هذا سيولد ملف anomaly_model.pkl داخل مجلد model/.


---

🚀 تشغيل الوكيل (Agent)

بعد التدريب:

cd ..

python agent.py

💡 سيبدأ الوكيل بمراقبة النظام، كشف السلوكيات المشبوهة، ورسم مخطط Anomaly، مع إرسال التنبيهات عبر Telegram.
