---
title: Cross Site Scripting
localeTitle: عبر موقع البرمجة
---
## عبر موقع البرمجة

Cross Site Scripting هو نوع من نقاط الضعف في تطبيق الويب بسبب عدم قيام مبرمج بتعقيم المدخلات قبل إخراج المدخلات إلى متصفح الويب (على سبيل المثال تعليق على مدونة). يتم استخدامه عادة لتشغيل جافا سكريبت الخبيثة في متصفح الويب للقيام بهجمات مثل سرقة ملفات تعريف الارتباط للجلسة بين إجراءات أخرى ضارة للحصول على امتيازات مستوى أعلى في تطبيق الويب.

### مثال عبر Scripting هجوم الموقع

تسمح المدونة للمستخدمين بوضع تعليقاتهم باستخدام علامات HTML ، إلا أن النص البرمجي الذي يمد المدونة لا يزيل علامات `<script>` تسمح لأي مستخدم بتشغيل javascript على الصفحة. يمكن للمهاجم استخدام هذه الميزة لصالح تشغيل javascript ضار في المستعرض. يمكن أن تصيب المستخدمين بالبرامج الضارة ، وتسرق ملفات تعريف الارتباط للجلسة ، والمزيد.

```HTML
<script>
  alert('Cross Site Scripting!');
</script>
``` 

### الدفاع عن موقع الويب الخاص بك من هجمات البرمجة عبر الموقع في PHP

في PHP هناك وظيفتان `htmlspecialchars()` ، `htmlspecialchars()` و `strip_tags()` ، مدمجة لحماية نفسك من هجمات البرمجة عبر الموقع.

`htmlspecialchars($string)` وظيفة `htmlspecialchars($string)` منع سلسلة HTML من العرض كملف HTML وعرضها كنص عادي لمتصفح الويب. **htmlspecialchars () مثال التعليمات البرمجية**

```PHP
<?php
$usercomment = "<string>alert('Cross Site Scripting!');</script>";
echo htmlspecialchars($usercomment);
``` 

الطريقة الأخرى هي `strip_tags($string, $allowedtags)` التي تزيل كل علامات HTML باستثناء علامات HTML التي قمت بإضافتها إلى القائمة البيضاء. من المهم أن نلاحظ أنه مع وظيفة `strip_tags()` يجب أن تكون أكثر حذراً ، هذه الوظيفة لا تمنع المستخدم من تضمين javascript كحلقة ارتباط ، سيكون عليك تطهير ذلك بمفردنا.

**code\_tags () مثال التعليمات البرمجية**

```php
<?php
$usercomment = "<string>alert('Cross Site Scripting!');</script>";
$allowedtags = "<p><a><h1><h2><h3>";
echo strip_tags($usercomment, $allowedtags);
``` 

**ضبط رأس الحماية X-XSS:**

في PHP ، يمكنك إرسال `X-XSS-Protection` Header الذي سيخبر المتصفحات بالتحقق من هجوم Scripting عبر موقع ويب منع الصفحة من التحميل. هذا لا يمنع جميع الهجمات النصية عبر الموقع فقط تنعكس منها ويجب استخدامها في تركيبة مع أساليب أخرى.

```PHP
<?php
header("X-XSS-Protection: 1; mode=block");
``` 

**كتابة وظيفة التعقيم الخاصة بك** خيار آخر ، إذا كنت ترغب في مزيد من التحكم في كيفية عمل التطهير ، هو كتابة وظيفة تعقيم HTML الخاصة بك ، وهذا لا يوصى به للمبتدئين PHP كخطأ من شأنه أن يجعل موقع الويب الخاص بك عرضة.

### الدفاع عن موقع الويب الخاص بك من هجمات البرمجة النصية عبر الموقع مع سياسة أمان المحتوى

إن اتباع نهج فعال لمنع هجمات البرمجة النصية عبر المواقع ، والتي قد تتطلب الكثير من التعديلات على تصميم وبرمجية تطبيق الويب الخاص بك ، هو استخدام سياسة أمن المحتوى.

#### عيّن سياسة أمان المحتوى كرأس HTTP

الطريقة الأكثر شيوعًا لتعيين سياسة أمان المحتوى هي عن طريق تعيينها مباشرةً في رأس HTTP. يمكن القيام بذلك عن طريق خادم الويب من خلال تعديل إعداداته أو إرساله عبر PHP.

**مثال على سياسة أمان المحتوى التي تم تعيينها في رأس HTTP**

```php
<?php
header("content-security-policy: default-src 'self'; img-src https://*; child-src 'none';");
``` 

#### عيّن سياسة أمان المحتوى كعلامات وصفية

يمكنك تضمين سياسة أمان المحتوى في HTML الخاص بالصفحة وتعيينها على أساس كل صفحة على حدة. تتطلب هذه الطريقة منك تعيين كل صفحة أو تفقد فائدة السياسة.

**مثال على سياسة أمان المحتوى التي تم تعيينها في علامة HTML الوصفية**

```HTML
<meta http-equiv="Content-Security-Policy" content="default-src 'self'; img-src https://*; child-src 'none';">
``` 

#### معلومات اكثر:

*   [OWASP Wiki - البرمجة عبر الموقع](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))
*   [php.net strip\_tags () دليل](https://secure.php.net/manual/en/function.strip-tags.php)
*   [php.net htmlspecialchars () دليل](https://secure.php.net/manual/en/function.htmlspecialchars.php)
*   [MDN - سياسة أمان المحتوى (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)