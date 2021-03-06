---
title: HTML5 Audio
localeTitle: HTML5 Audio
---
## HTML5 Audio

До появления HTML5 аудиофайлы воспроизводились в браузере с помощью подключаемого модуля, такого как Adobe Flash. HTML-код элемента используется для вставки звукового контента в документы. Он может содержать один или несколько источников звука, представленных с использованием атрибута src или [исходного](source) элемента

Следующий фрагмент кода добавляет аудиофайл с именем файла `tutorial.ogg` или `tutorial.mp3` .  Элемент указывает альтернативные аудиофайлы, которые может выбрать браузер. В браузере будет использоваться первый распознанный формат.

#### Пример 1

```html

<audio controls> 
  <source src="tutorial.ogg" type="audio/ogg"> 
  <source src="tutorial.mp3" type="audio/mpeg"> 
 Your browser does not support the audio element. 
 </audio> 
```

#### Пример 2.

```html

<audio src="https://s3.amazonaws.com/freecodecamp/simonSound1.mp3" controls loop autoplay> 
 </audio> 
```

Атрибут `controls` включает в себя элементы управления аудио, такие как воспроизведение, пауза и громкость. Если вы не используете этот атрибут, никакие элементы управления не будут показаны.

Элемент `<source>` позволяет указать альтернативные аудиофайлы, которые может выбрать браузер. В браузере будет использоваться первый распознаваемый формат. Текст между тегами `<audio>` и `</audio>` может отображаться в браузере, который не поддерживает элемент HTML5 `<audio>` .

Атрибут autoplay автоматически воспроизводит ваш аудиофайл в фоновом режиме. Считается лучшей практикой, позволяющей посетителям выбирать воспроизведение аудио.

Атрибут preload указывает, что браузер должен делать, если плеер не настроен на автовоспроизведение.

Атрибут loop будет воспроизводить ваш аудиофайл в непрерывном цикле, если упомянутый

Поскольку это html5, некоторые браузеры не поддерживают его. Вы можете проверить его на странице https://caniuse.com/#search=audio

#### Дополнительная информация:

https://caniuse.com/#search=audio

https://www.w3schools.com/html/html5\_audio.asp

https://msdn.microsoft.com/en-us/library/gg589529(v=vs.85).aspx
