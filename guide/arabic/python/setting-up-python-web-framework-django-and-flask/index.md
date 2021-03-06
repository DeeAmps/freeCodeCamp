---
title: Setting Up Python Web Framework Django and Flask
localeTitle: إعداد Python Web Framework Django وقارورة
---
في هذه المقالة ، سنناقش كيفية تثبيت [Django](https://www.djangoproject.com/) و [Flask](http://flask.pocoo.org/) - وهما إطارين على شبكة الإنترنت شعبية مكتوبة في بايثون.

ربما كنت على دراية بالفعل بالاستخدام الواسع النطاق والدعم المجتمعي لبيثون ؛ في تطوير الويب. قد تكون على دراية بماهية إطار الويب ؛ والخيارات المتاحة لبيثون.

في حالة عدم صحة هذه الافتراضات ، قد ترغب في إلقاء نظرة على مقالة wiki هذه. إذا كنت جميعًا عالقين ، فدعونا نذهب من خلال وضع أطر بيثون على الويب في جهاز التطوير المحلي لديك.

ولكن سيكون من غير العدل أن نتجاهل تمامًا مناقشة [Python 2 vs Python 3](http://docs.python-guide.org/en/latest/starting/which-python/#the-state-of-python-2-vs-3) .

## بيئة افتراضية

قبل تثبيت Django ، سنقوم بتثبيت أداة مفيدة للغاية للمساعدة في الحفاظ على بيئة الترميز الخاصة بك مرتبة على جهاز الكمبيوتر الخاص بك. من الممكن تخطي هذه الخطوة ، ولكنها موصى بها للغاية. بدءا من أفضل إعداد ممكن سيوفر لك الكثير من المتاعب في المستقبل!

لذلك ، دعونا إنشاء بيئة افتراضية (وتسمى أيضا virtualenv). سيقوم Virtualenv بعزل إعداد Python / Django على أساس كل مشروع. وهذا يعني أن أي تغييرات تجريها على موقع ويب واحد لن تؤثر على أي تغييرات أخرى تقوم بتطويرها أيضًا. أنيق ، صحيح؟

لمزيد من المعلومات حول البيئات الافتراضية ، انظر قسم relevent [هنا](https://guide.freecodecamp.org/python/virtual-environments/) .

## تغليف

إذا كنت قد قمت بالفعل بتثبيت برنامج `pip` فببساطة:

```
$ pip install django
``` 

بعد اكتمال التثبيت ، يمكننا إنشاء مشروع جديد:

```
$ django-admin startproject myproject
$ cd myproject
$ python manage.py runserver
``` 

انتقل إلى `http://localhost:8000` ! :صاروخ:

لقد نجحنا في تثبيت إطار الويب لحاجتنا. ومع ذلك ، لم تكتمل بعد. معظم تطبيقات الويب تعتمد على المحتوى والبيانات - لذا نحتاج إلى تخزين البيانات. أو ، قاعدة بيانات ، إذا صح التعبير.

في المقالة التالية ، سنناقش كيفية تثبيت PostgreSQL واستخدامه مع تطبيق ويب Python الخاص بنا.

نقطة للتفكير - لقد تم استخدام `pip` بكثافة ، ولكن بالكاد قال أي شيء حول هذا الموضوع. حسنا ، في الوقت الحالي ، إنها مجرد مدير حزم مثل `npm` . لديها بعض الاختلافات مع `npm` ؛ ولكن ، لا داعي للقلق بشأن ذلك الآن. إذا كنت مهتمًا ، فيمكنك [`pip` وثائق `pip` الرسمية](http://pip-python3.readthedocs.org/en/latest/index.html) .

_إذا كانت لديك اقتراحات أو أسئلة ، [فانتقل](https://gitter.im/FreeCodeCamp/FreeCodeCamp) إلينا على [قناة gitter](https://gitter.im/FreeCodeCamp/FreeCodeCamp)_ .