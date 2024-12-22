Разбираем мощные, но часто игнорируемые атрибуты HTML, способные значительно улучшить пользовательский опыт и SEO вашего сайта. От многоязычности до удобства заполнения форм – все, что нужно современному разработчику

## hreflang

hreflang – атрибут для указания языка ресурса, связанного с элементами `<a>` или `<link>`. Он похож на атрибут `lang`, но применяется специально для ссылок.

### Зачем нужен hreflang:

- **Улучшение пользовательского опыта** – позволяет автоматически перенаправлять пользователей на страницу на их языке, исключая необходимость ручного переключения.
- **SEO** – помогает поисковым системам понять, какие версии страницы предназначены для разных языков или регионов. Например, англоязычные пользователи получат версию сайта на английском, а русскоязычные – на русском.

### Как использовать hreflang:

Указание языка страницы. Используйте код языка (например, `en` для английского) в атрибуте `hreflang` для элементов `<a>` или `<link>` :
```html
<a href="https://example.com" hreflang="en">English Website</a>
```

Можно указать региональный вариант языка, если он существует – например, британский английский (`en-GB`):
```html
<a href="https://example.at" hreflang="en-GB">English Website</a>
```
Несколько языков на сайте. Если сайт доступен на нескольких языках, укажите `hreflang` для каждой языковой версии. Атрибут `x-default` используется для версии сайта по умолчанию:
```html
<link href="https://example.com" rel="alternate" hreflang="x-default" /> 
<link href="https://example.com/de" rel="alternate" hreflang="de" />
```

Переключатель языков. Используйте `hreflang` в переключателе языков:
```html
<a href="https://example.com" hreflang="x-default">English</a> 
<a href="https://example.com/de" hreflang="de">German</a>
```

Поддержка технологий для людей с ограниченными возможностями. Добавьте атрибут `lang` для улучшения восприятия текста пользователями экранных дикторов. Кроме того, многие переключатели языков используют текст `lang` в ссылках:
```html
<a href="https://example.com" hreflang="x-default">English</a> 
<a href="https://example.com/de" hreflang="de" lang="de">Deutsch</a>
```

Подсветка активной ссылки. Еще один способ улучшения доступности – добавление `aria-current="true"` к текущей активной ссылке:
```html
<a href="https://example.com" hreflang="x-default" aria-current="true">English</a> <a href="https://example.com/de" hreflang="de" lang="de">Deutsch</a>
```

## translate

Атрибут `translate` указывает, нужно ли переводить содержимое элемента.

### Зачем использовать translate

Большая часть текста на сайте легко переводится Google Translate, если язык страницы отличается от языка браузера. Однако автоматический перевод может исказить значение специфических или узкоспециализированных терминов. Кроме того, бывают случаи, когда перевод нежелателен – нет смысла переводить названия компаний, адреса электронной почты, примеры кода и т. п.

### Как использовать атрибут translate

Атрибут можно применять к любому HTML-элементу. Используйте:

1. `translate="yes" (или translate="")` – для включения перевода (значение по умолчанию).
2. `translate="no"` – для исключения элемента из перевода.
```html
<!-- Original German text --> 
<p> <span>Wien<span> ist (wieder) die lebenswerteste Stadt der Welt! </p> 
<p> <span translate="no">Wien<span> ist (wieder) die lebenswerteste Stadt der Welt! </p> 
<!-- What it would look like translated into English --> 
<p> <span>Vienna<span> named world's most liveable city (again)! </p> 
<p> <span translate="no">Wien<span> named world's most liveable city (again)! </p>
```

## reversed

Атрибут `reversed` используется для отображения нумерованного списка `<ol>` в обратном порядке, начиная с самого большого. Работает только с `<ol>` и не применяется к ненумерованным спискам `<ul>`.

### Зачем использовать reversed

Для отображения обратного отсчета, рейтингов, списков победителей и т.п., начиная с последнего места и заканчивая первым. При этом:

1. Элементы списка остаются в том же порядке в HTML-коде (визуальный и семантический порядок совпадают).
2. Меняются только номера, которые отображаются на экране.

### Как использовать reversed

Добавьте атрибут `reversed` к элементу `<ol>`:
```html
<ol reversed> 
	<li>Cookies</li> 
	<li>Crema Catalana</li> 
	<li>Tiramisu</li> 
	<li>Pastel de Nata</li> 
	<li>Sacher cake</li> 
</ol>
```

Экранные дикторы будут читать список в порядке, указанном в HTML-документе, но с учетом правильной нумерации: «5. Cookies, 4. Crema Catalana и т. д.»

## controls

Атрибут controls используется для отображения стандартных элементов управления воспроизведением видео или аудио в браузере. Он добавляется к тегам `<video>` или `<audio>`.

### Зачем нужен controls

Элементы управления позволяют пользователям воспроизводить, приостанавливать, перематывать и изменять громкость. Это особенно важно для пользователей, которые:

1. Испытывают дискомфорт из-за неожиданного воспроизведения.
2. Предпочитают контролировать громкость или отключить звук.
3. Хотят переключиться на полноэкранный режим или включить субтитры.

### Как использовать controls

Просто добавьте атрибут controls к тегу `<video>` или `<audio>`. Пример для видео:
```html

<video controls> 
	<source src="movie.mp4" type="video/mp4"> 
	<source src="movie.ogg" type="video/ogg"> 
	<track kind="captions" src="sampleCaptions.vtt" srclang="en" /> 
	<track kind="subtitles" src="sampleSubtitles_en.vtt" srclang="en" /> 
	<track kind="subtitles" src="sampleSubtitles_de.vtt" srclang="de" /> 
Your browser does not support the video tag. 
</video>
```

## autocomplete

Атрибут `autocomplete` позволяет браузеру автоматически заполнять значения форм на основе ранее введенных данных. Он применяется к элементам `<form>`, `<input>`, `<select>` и `<textarea>`.

### Зачем использовать autocomplete:

1. Удобство и экономия времени. Пользователи могут быстро заполнять формы, используя ранее сохраненные данные (например, имя, адрес или e-mail), без необходимости повторного ввода.
2. Доступность. Помогает людям с когнитивными нарушениями, ограниченной подвижностью, дефицитом внимания, слабым зрением или слепотой. Экранные дикторы используют атрибут `autocomplete` для помощи пользователям в понимании назначения поля и автоматическом вводе данных.
3. Улучшение юзабилити. Автоматическое заполнение уменьшает количество ошибок, снижает нагрузку на пользователя и делает формы более удобными.

### Как использовать autocomplete

Атрибут принимает различные значения для управления автозаполнением:

1. Отключение автозаполнения. Установите значение `off`, чтобы браузер не предлагал сохранять или использовать данные для этого поля (некоторые менеджеры паролей могут игнорировать это ограничение):
```html
<label for="email">E-Mail</label> 
<input name="email" id="email" type="email" autocomplete="off" />
```

Включение автозаполнения. Установите значение on, чтобы браузер заполнял поле автоматически, если подходящие данные были сохранены. Если не указать конкретное значение, браузер самостоятельно решит, как интерпретировать поле:

```html
<form action="/" autocomplete="on"> 
	<label for="firstname">First Name</label> 
		<input type="text" name="firstname" id="firstname" /> 
	<label for="lastname">Last Name</label> 
		<input type="text" name="lastname" id="lastname" /> 
	<label for="email">Email</label> <input type="email" name="email" id="email" /> 
</form>
```

Оптимальное использование. Отсутствие или некорректное указание значения `autocomplete` может усложнить заполнение форм – используйте конкретные значения из списка доступных типов автозаполнения. Это помогает браузерам и технологиям для людей с ограниченными возможностями точно понимать назначение поля:

```html
<form action="/" autocomplete="on"> 
	<label for="firstName">First Name</label> 
		<input autocomplete="given-name" name="firstName" id="firstName" type="text" /> 
	<label for="lastName">Last Name</label> 
		<input autocomplete="family-name" name="lastName" id="lastName" type="text" /> 
	<label for="email">Email</label> 
	<input autocomplete="email" name="email" id="email" type="email" /> 
</form>
```