# تحويل My Video Library لتطبيق يتثبّت على الموبايل (مجاناً)

## الخطوة 1 — تعديل بسيط في Apps Script
افتح مشروع السكربت، ودوّر على دالة `doGet` وخلّي آخر سطر فيها بالشكل ده:

```javascript
function doGet(e) {
  return HtmlService.createHtmlOutputFromFile('Index')   // نفس اسم الملف اللي عندك
    .setTitle('My Library')
    .addMetaTag('viewport', 'width=device-width, initial-scale=1')
    .setXFrameOptionsMode(HtmlService.XFrameOptionsMode.ALLOWALL); // ⬅️ ده المهم
}
```
لو بتستخدم `createTemplateFromFile(...).evaluate()` حط `.setXFrameOptionsMode(...)` بعد `.evaluate()`.

بعدين: **Deploy ← Manage deployments ← ✏️ ← Version: New version ← Deploy**
(كده اللينك بيفضل زي ما هو).

## الخطوة 2 — رفع الملفات على GitHub Pages (مجاني)
1. اعمل حساب على github.com لو مش عندك.
2. **New repository** ← اسمه مثلاً `mylibrary` ← خليه **Public** ← Create.
3. **Add file ← Upload files** وارفع كل الملفات دي (مع فولدر `icons`) ← Commit.
4. **Settings ← Pages ← Branch: main ← / (root) ← Save**.
5. بعد دقيقة هيظهر لينك زي: `https://USERNAME.github.io/mylibrary/`

## الخطوة 3 — ابعت اللينك
اللينك ده هو بتاعك زي `crm.diamondeye.eg/install`:
- يفتح صفحة التثبيت بالخطوات.
- على أندرويد/الكمبيوتر يظهر زرار "ثبّت التطبيق دلوقتي".
- على الآيفون يوريه خطوات Safari.
- بعد التثبيت الأيقونة تفتح التطبيق full screen من غير شريط المتصفح.

## ملاحظات
- لو عملت Deployment جديد بلينك مختلف، غيّر `APP_URL` في `index.html`.
- عاوز تغيّر الاسم: `manifest.json` + `install.html`. والأيقونة: بدّل الصور في `icons` بنفس المقاسات (192 و 512).
- عاوز دومين خاص زي `app.yourname.com`؟ ممكن تربطه في GitHub Pages مجاناً (الدومين نفسه بس اللي بفلوس).
