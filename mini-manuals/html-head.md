## 🤯 HEAD

> Простое руководство по HTML-элементам в `<head>`

## Оглавление

- [Рекомендуемый минимум](#рекомендуемый-минимум)
- [Элементы](#элементы)
- [Мета](#мета)
- [Предзагрузка](#предзагрузка)
- [Роботы, СЕО](#роботы-сео)
- [Google, Yandex](#google-yandex)
- [Ссылки](#ссылки)
- [Иконки](#иконки)
- [Микроразметка](#микроразметка)
  - [Facebook Open Graph](#facebook-open-graph)
  - [Twitter Card / Privacy](#twitter-card--privacy)
  - [Schema.org](#schemaorg)
  - [JSON-LD](#json-ld)
  - [OEmbed](#oembed)
- [Браузеры / Платформы](#браузеры--платформы)
  - [Apple iOS](#apple-ios)
  - [Google Android](#google-android)
  - [Google Chrome](#google-chrome)
  - [Microsoft Internet Explorer](#microsoft-internet-explorer)
- [CSRF атаки](#csrf-атаки)
- [Подсказки HTTP клиентов](#подсказки-http-клиентов)

## Рекомендуемый минимум

Ниже приведены основные элементы для любого веб-документа (веб-сайта/приложения):

```html
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <!--
   Вышеуказанные 2 мета-тега *должны* стоять как можно раньше в <head>.
   для обеспечения правильного отображения документов.
  -->
  <title>Заголовок страницы</title>
</head>
```

- `meta charset` - определяет кодировку веб-сайта, стандартом является `utf-8`.

- `meta name="viewport"` - настройки viewport, связанные с мобильной отзывчивостью

- `width=device-width` - физическая ширина устройства (отлично подходит для мобильных устройств!)

- `initial-scale=1` - начальный масштаб, 1 означает отсутствие масштабирования

```html
<!-- viewport-fit для управления безопасной зоны
(изогнутые края экрана гаджетов) -->
<meta
  name="viewport"
  content="width=device-width, initial-scale=1, viewport-fit=cover"
/>
```

- `contain`: вьюпорт должен полностью вмещать веб-контент.
- `cover`: веб-контент должен полностью покрывать вьюпорт.
- `auto`: значение по умолчанию, работает как `contain`.

[Подробнее о WebView](https://css-live.ru/articles/ponimanie-vyuporta-webview-v-ios-11.html)

[⬆ вернуться к началу](#оглавление)

## Элементы

Допустимые элементы `<head>` включают `base`, `link`, `meta`, `noscript`, `script`, `style`, `template` и `title`.

Эти элементы предоставляют информацию о том, как документ должен восприниматься и отображаться веб-технологиями, например, браузерами, поисковыми системами, ботами и так далее.

```html
<!--
 Кодировка символов в пространстве UTF-8 (чтобы все символы и эмодзи
отображались правильно.
-->
<meta charset="utf-8" />

<!-- Установите заголовок документа -->
<title>Заголовок страницы</title>

<!-- Базовый URL для всех относительных URL в документе -->
<base href="https://example.com/page.html" />

<!-- Ссылка на внешний файл CSS (+для принтеров) -->
<link rel="stylesheet" href="style.css" />
<link rel="stylesheet" href="/assets/css/print.css" media="print" />

<!-- Добавление CSS в документ. Используется для важной стилизации -->
<style>
  /* ... */
</style>

<!-- Ссылка на внешний JavaScript файл (defer/async) -->
<script src="script.js"></script>

<!-- Используется для добавление JS в документ-->
<script>
  // функция(и) идут здесь
</script>

<!-- Используется на случай если JavaScript отключен в браузере -->
<noscript>
  <!-- Альтернатива, когда JS отключен -->
</noscript>

<!-- Используется для объявления HTML-фрагментов, которые могут быть клонированы и вставлены в документ. 
Если указан в <head>, то <template> может содержать только метаданные -->
<template> </template>
```

[⬆ вернуться к началу](#оглавление)

## Мета

```html
<!--
 Позволяет контролировать, откуда загружаются ресурсы.
 Поместите как можно раньше в <head>, так как тег 
 применяется только к ресурсам, которые объявлены после него.
-->
<meta http-equiv="Content-Security-Policy" content="default-src 'self'" />

<!-- Название веб-приложения (должно использоваться только в том случае, если веб-сайт используется как приложение) -->
<meta name="application-name" content="Имя приложения" />.

<!-- Цвет вкладки для Chrome на Android, Vivaldi, Safari 15 -->
<meta name="theme-color" content="#4285f4" />

<!-- Краткое описание документа (ограничение до 150 символов) 
Это содержимое *может* использоваться в результатах поисковых систем. -->
<meta name="description" content="Описание страницы" />.

<!-- Список ключевых слов (СЕО, возможно устаревший) -->
<meta name="keywords" content="ваши, теги" />

<!-- Ссылка на JSON-файл, в котором указаны данные для "установки" веб-приложения -->
<link rel="manifest" href="manifest.json" />
<link rel="manifest" href="manifest.webmanifest" />

<!-- Соль (PHP, хеширование паролей) -->
<meta name="salt" content="21f157b19463e98d0e9723cf486d620a" />

<!-- Язык документа -->
<meta name="language" content="Russian" />

<!-- Указывает документ, который будет отображаться в определенном фрейме -->
<meta http-equiv="Window-Target" content="_value" />
```

[Про соль подробнее](https://www.php.net/manual/ru/faq.passwords.php#faq.passwords.salt)

> 💡 Для СЕО рекомендуется уделять внимание в первую очередь более влиятельным тегам — **Title**, **Description** — и по желанию заполнять Keywords.

## Предзагрузка

<!-- FIXME прочитать хабр https://habr.com/ru/post/445264/  -->

```html
<!-- Prefetching, preloading, prebrowsing -->
<!-- Дополнительная информация: https://css-tricks.com/prefetching-preloading-prebrowsing/ -->
<link rel="preconnect" href="https://www.example.com/" />
<link rel="dns-prefetch" href="//example.com/" />

<link rel="prefetch" href="https://www.example.com/" />
<link rel="preload" href="image.png" as="image" />
<link rel="prerender" href="https://example.com/" />.
<link rel="modulepreload" href="super-critical-stuff.js" />
<!-- Предзагрузка модулей -->
```

## РОБОТЫ, СЕО

```html
<!-- Управление поведением поисковых машин при осмотре и индексации сайта -->
<meta name="robots" content="index,follow" /><!-- Все поисковые системы -->
<meta name="googlebot" content="index,follow" /><!-- Специфика Google -->

<!-- Как часто посещать сайт роботу-->
<meta content="10 day" name="revisit" />

<!-- Дата последнего изменения документа -->
<meta name="revised" content="Sunday, July 18th, 2010, 5:15 pm" />

<!-- Используется как description, но для научных статей-->
<meta name="abstract" content="" />
<meta name="topic" content="" />
<meta name="summary" content="" />

<!-- Для обратной связи -->
<meta name="reply-to" content="email@hotmail.com" />
```

Для роботов есть несколько значений:  
(значения можно писать через запятую `content="max-snippet:-1, max-image-preview:large, max-video-preview:-1"`.)

- `all` - нет ограничений на индексирование и показ контента.
- `noindex` - не показывать эту страницу в результатах поиска.
- `nofollow` - не выполнять переход по ссылкам на странице.
- `none` - эквивалент noindex, nofollow.
- `noarchive` - запрещает показывать ссылку на кеш в результатах поиска.
- `nosnippet` - не показывать в результатах поиска текстовый фрагмент или видео.
- `max-snippet: [number]` - ограничение на количество символов в текстовом фрагменте
- `max-image-preview: [setting]` - определяет максимальный размер изображений, которые могут показываться в результатах поиска для этой страницы.
- `max-video-preview: [number]` - задает для фрагмента видео со страницы ограничение по длительности в секундах при показе в результатах поиска.
- `notranslate` - не предлагать перевести эту страницу в результатах поиска.
- `noimageindex` - не индексировать изображения на странице.
- `unavailable_after: [date/time]` - запрещает показывать страницу в результатах поиска после даты и времени.
- `noyaca` - запрет на использование информации из Яндекс.Каталога для описания в сниппете
- `noodp` — запрет на использование описания из dMoz для сниппета;
- `noydir` — запрет на использование описания из Yahoo! Directory для сниппета.

[Подробнее о Robots-metatags](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

### Google, Yandex

```html
<!-- Указывает Google не показывать поисковую строку sitelinks -->
<meta name="google" content="nositelinkssearchbox" />

<!-- Указывает Google не переводить документ -->
<meta name="google" content="notranslate" />
<!-- Проверить право собственности сайта -->
<meta
  name="google-site-verification"
  content="verification_token"
/><!-- Google Search Console -->

<meta
  name="yandex-verification"
  content="verification_token"
/><!-- Яндекс Вебмастерам -->

<!-- Укажите программное обеспечение, использованное для создания документа (например, WordPress, Dreamweaver) -->
<meta name="generator" content="название программного обеспечения" />

<!-- Краткое описание темы вашего документа -->
<meta name="subject" content="тема вашего документа" />

<!-- Дает общую возрастную оценку, основанную на содержании документа -->
<meta name="rating" content="General" />

<!-- Позволяет контролировать, как передается информация о реферере -->
<meta name="referrer" content="no-referrer" />

<!-- Отключить автоматическое определение и форматирование возможных телефонных номеров -->
<meta name="format-detection" content="phone=no" />

<!-- Полностью отказаться от предварительной выборки DNS, установив значение "off" -->
<meta http-equiv="x-dns-prefetch-control" content="off" />

<!-- Гео-теги -->
<meta name="ICBM" content="широта, долгота" />.
<meta name="geo.position" content="широта;долгота" />
<meta
  name="geo.region"
  content="country[-state]"
/><!-- Код страны (ISO 3166-1): обязательный, код штата (ISO 3166-2): необязательный; например, content="US" / content="US-NY" -->
<meta
  name="geo.placename"
  content="city/town"
/><!-- например, content="New York City" -->

<!-- Монетизация веб-сайтов https://webmonetization.org/docs/getting-started -->
<meta name="monetization" content="$paymentpointer.example" />

<!-- Подсказывает, что сайт оптимизирован для мобильных устройств-->
<meta name="HandheldFriendly" content="true" />

<!-- Указывает автора документа -->
<meta name="author" content="Nikolai Shabalin" />

<!-- Принадлежность авторских прав-->
<meta name="copyright" content="Nikolai Shabalin" />

<!-- Создатель документа -->
<meta name="creator" content="Nikolai Shabalin" />

<!-- Владелец -->
<meta name="owner" content="" />

<!-- Регистрация доменного имени -->
<meta name="parking" content="имя регистратора" />
```

- 📖 [Мета-теги, которые понимает Google](https://support.google.com/webmasters/answer/79812?hl=en)
- 📖 [WHATWG Wiki: MetaExtensions](https://wiki.whatwg.org/wiki/MetaExtensions)
- 📖 [Геотеги в Википедии](https://en.wikipedia.org/wiki/Geotagging#HTML_pages)

[⬆ вернуться к началу](#оглавление)

## Ссылки

```html
<!-- Помогает предотвратить проблемы дублированного контента -->
<link rel="canonical" href="https://example.com/article/?page=2" />

<!-- Предыдущий и следующий документы в серии документов, соответственно -->
<link rel="prev" href="https://example.com/article/?page=1" />
<link rel="next" href="https://example.com/article/?page=3" />

<!-- Перезагружает страницу через указанное количество секунд -->
<meta http-equiv="Refresh" content="20" />
<meta http-equiv="Refresh" content="20; URL=page4.html" />
<!-- Перезагружает к указанной странице -->

<!-- Ссылки на AMP HTML (Accelerated Mobile Pages) версию текущего документа -->
<link rel="amphtml" href="https://example.com/path/to/amp-version.html" />

<!-- Ссылки на информацию (эксперем.) об авторе (авторах) документа -->
<link rel="author" href="humans.txt" />
```

[Canonical, подробнее](https://vc.ru/seo/72710-atribut-rel-canonical)

```html
<!-- Дает ссылку на место в вашем документе, 
который может быть на другом языке -->
<link rel="alternate" href="https://es.example.com/" hreflang="es" />

<!-- Ссылки на документ, описывающий коллекцию записей, документов или других материалов, представляющих исторический интерес -->
<link rel="archives" href="https://example.com/archives/" />

<!-- Ссылки на ресурс верхнего уровня в иерархической структуре -->
<link rel="index" href="https://example.com/article/" />

<!-- Обеспечивает самостоятельную ссылку - полезно, когда 
документ имеет несколько возможных ссылок -->
<link
  rel="self"
  type="application/atom+xml"
  href="https://example.com/atom.xml"
/>

<!-- Используется, когда для ведения блога используется сторонний сервис -->
<link
  rel="EditURI"
  href="https://example.com/xmlrpc.php?rsd"
  type="application/rsd+xml"
  title="RSD"
/>

<!-- Уведомляет URL, когда вы ссылаетесь на него в вашем документе. 
Дополнительная информация на https://webmention.net -->
<link rel="webmention" href="https://example.com/webmention" />

<!-- Позволяет размещать сообщения на вашем собственном 
домене с помощью клиента Micropub. Более подробная информация на https://indieweb.org/Micropub  -->
<link rel="micropub" href="https://example.com/micropub" />

<!-- Позволяет использовать ваш сайт с [социальным ридером](https://indieweb.org/social_reader) на базе Microsub. Более подробная информация на https://indieweb.org/Microsub -->
<link rel="microsub" href="https://example.com/microsub" />

<!-- Open Search -->
<link
  rel="search"
  href="/open-search.xml"
  type="application/opensearchdescription+xml"
  title="Заголовок поиска"
/>.

<!-- Фиды RSS -->
<link
  rel="alternate"
  href="https://feeds.feedburner.com/example"
  type="application/rss+xml"
  title="RSS"
/>
<link
  rel="alternate"
  href="https://example.com/feed.atom"
  type="application/atom+xml"
  title="Atom 0.3"
/>
```

[⬆ вернуться к началу](#оглавление)

## Иконки

```html
<!-- Для IE 10 и ниже -->
<link rel="icon" href="favicon.ico" /><!-- 32×32 -->
```

`<link rel="icon" href="favicon.ico">` - необязательно указывать в `<head>`. Любой сервер ищет `favicon.ico`, но для этого `favicon.ico` обязательно нужно положить в корень проекта. От `.ico` лучше не отказываться, так как могут перестать работать иконки, например в RSS-читалках. В `.ico` поддерживается прозрачность.
На данный момент в Хром есть [баг](https://bugs.chromium.org/p/chromium/issues/detail?id=1162276). Если в проекте подключены `ICO` и `SVG` версии, то всё равно предпочтение отдаётся `ICO`.

```html
<link rel="icon" href=" icon.svg" type="image/svg+xml" />
```

Преимущество SVG-фавиконки в том, что, помимо того, что он векторный, он может подстраиваться под тёмную тему с помощью ` @media (prefers-color-scheme: dark)`. [Поддержка векторных фавиконок](https://caniuse.com/link-icon-svg).

```html
<!-- IOS 8+ -->
<link rel="apple-touch-icon" href="apple-touch-icon.png" /><!-- 180×180 -->
```

Используется для отображения ярлыка на домашнем экране IPhone и IPad.

Выше указаны три версии для фавиконки фавиконки, но можно добавить ещё 2, чтобы учесть большинство современных браузеров. Чтобы не увеличивать HTML другие фавиконки добавляют в веб-манифест

```html
<link rel="manifest" href="/manifest.webmanifest" />
```

_manifest.webmanifest_

```json
{
  "icons": [
    { "src": "192.png", "type": "image/png", "sizes": "192x192" },
    { "src": "12.png", "type": "image/png", "sizes": "512x512" }
  ]
}
```

- 📖 [Все о фавиконах (и сенсорных иконках)](https://bitsofco.de/all-about-favicons-and-touch-icons/)
- 📖 [Создание прикрепленных иконок вкладок](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/pinnedTabs/pinnedTabs.html)
- 📖 [Favicon Cheat Sheet](https://github.com/audreyr/favicon-cheat-sheet)
- 📖 [Иконки и цвета браузера](https://developers.google.com/web/fundamentals/design-and-ux/browser-customization/)
- 📖 [Как создать Favicon в 2021 году: шесть файлов, которые подходят большинству потребностей](https://evilmartians.com/chronicles/how-to-favicon-in-2021-six-files-that-fit-most-needs)

[⬆ вернуться к началу](#оглавление)

## Микроразметка

### Facebook Open Graph (og:)

> Большинство материалов передается на Facebook в виде URL, поэтому важно, чтобы вы разметили свой сайт тегами Open Graph, чтобы взять под контроль то, как ваши материалы появляются на Facebook. [Подробнее о разметке Facebook Open Graph](https://developers.facebook.com/docs/sharing/webmasters#markup)

```html
<meta property="fb:app_id" content="123456789" />
<meta property="og:url" content="https://example.com/page.html" />
<meta property="og:type" content="website" />
<meta property="og:title" content="Заголовок содержимого" />
<meta property="og:image" content="https://example.com/image.jpg" />
<meta
  property="og:image:alt"
  content="Описание того, что находится на изображении (не подпись)"
/>
<meta property="og:description" content="Описание" />
<meta property="og:site_name" content="Название сайта" />
<meta property="og:locale" content="ru_RU" />
<meta property="article:author" content="" />
```

- 📖 [Open Graph protocol](http://ogp.me/)
- 🛠 Протестируйте свою страницу с помощью [Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)

### Twitter Card / Privacy

> С помощью Twitter Cards вы можете прикреплять к твитам фотографии, видео и мультимедийные файлы, тем самым способствуя привлечению трафика на ваш сайт. [Подробнее о Twitter Cards](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards)

```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@site_account" />
<meta name="twitter:creator" content="@individual_account" />
<meta name="twitter:url" content="https://example.com/page.html" />
<meta name="twitter:title" content="Заголовок контента" />.
<meta
  name="twitter:description"
  content="Описание контента менее 200 символов"
/>. <meta name="twitter:image" content="https://example.com/image.jpg" />.
<meta
  name="twitter:image:alt"
  content="Текстовое описание изображения, передающее его суть пользователям с ослабленным зрением. Максимум 420 символов."
/>

<!-- запретить Twitter использовать информацию о вашем сайте в целях персонализации -->
<meta name="twitter:dnt" content="on" />
```

- 📖 [Начало работы с карточками - Twitter Developers](https://dev.twitter.com/cards/getting-started)
- 🛠 Проверьте свою страницу с помощью [Twitter Card Validator](https://cards-dev.twitter.com/validator)

### Schema.org

```html
<html lang="" itemscope itemtype="https://schema.org/Article">
  <head>
    <link rel="author" href="" />
    <link rel="publisher" href="" />
    <meta itemprop="name" content="Заголовок контента" />
    .
    <meta
      itemprop="description"
      content="Описание содержимого менее 200 символов"
    />
    .
    <meta itemprop="image" content="https://example.com/image.jpg" />
  </head>
</html>
```

**Примечание:** Эти мета-теги требуют добавления атрибутов `itemscope` и `itemtype` к тегу `<html>`.

- 📖 [Начало работы - schema.org](https://schema.org/docs/gs.html)
- 🛠 Протестируйте свою страницу с помощью [Rich Results Test](https://search.google.com/test/rich-results)

### JSON-LD

Может использоваться компанией для того, чтобы ваш сайт отображался в графе знаний, когда кто-то набирает ваш запрос. (это панель справа от результатов поиска, которая обычно появляется у крупных брендов.)

```
<script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "Article",
    "author": {
      "@type": "Person",
      "name": "Your Name"
    },
    "publisher": {
      "@type": "Organization",
      "name": "Your Organization"
    },
    "headline": "Article Headline",
    "image": "https://example.com/image.jpg",
    "datePublished": "2020-02-05T08:00:00+08:00",
    "dateModified": "2020-03-05T09:20:00+08:00"
  }
</script>
```

- [Спецификация](https://www.w3.org/TR/json-ld11/)
- [Официальный сайт](https://json-ld.org/)
- [Документация от Google](https://developers.google.com/search/docs/data-types/article)

[⬆ вернуться к началу](#оглавление)

### OEmbed

```html
<link
  rel="alternate"
  type="application/json+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=json"
  title="Профиль oEmbed: JSON"
/>
<link
  rel="alternate"
  type="text/xml+oembed"
  href="https://example.com/services/oembed?url=http%3A%2F%2Fexample.com%2Ffoo%2F&amp;format=xml"
  title="oEmbed Profile: XML"
/>
```

- 📖 [oEmbed format](https://oembed.com/)

## Браузеры / Платформы

### Apple iOS

```html
<!-- Баннер умного приложения -->
<meta
  name="apple-itunes-app"
  content="app-id=APP_ID,affiliate-data=AFFILIATE_ID,app-argument=SOME_TEXT"
/>

<!-- Отключить автоматическое определение и форматирование возможных телефонных номеров -->
<meta name="format-detection" content="phone=no" />

<!-- Иконка запуска (180x180px или больше) -->
<link rel="apple-touch-icon" href="/path/to/apple-touch-icon.png" />

<!-- Изображение экрана запуска -->
<link rel="apple-touch-startup-image" href="/path/to/launch.png" />

<!-- Заголовок значка запуска -->
<meta name="apple-mobile-web-app-title" content="Название приложения" />.

<!-- Включить автономный (полноэкранный) режим -->
<meta name="apple-mobile-web-app-capable" content="yes" />

<!-- Внешний вид строки состояния (не влияет, если не включен автономный режим) -->
<meta name="apple-mobile-web-app-status-bar-style" content="black" />

<!-- Глубокое связывание приложений iOS -->
<meta
  name="apple-itunes-app"
  content="app-id=APP-ID, app-argument=http/url-sample.com"
/>
<link rel="alternate" href="ios-app://APP-ID/http/url-sample.com" />
```

- 📖 [Configuring Web Applications](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)

### Google Android

```html
<!-- Цветовая тем приложения -->
<meta name="theme-color" content="#E64545" />

<!-- Добавить на главный экран -->
<meta name="mobile-web-app-capable" content="yes" />
<!-- Дополнительная информация: https://developer.chrome.com/multidevice/android/installtohomescreen -->

<!-- Глубокое связывание приложений Android -->
<meta name="google-play-app" content="app-id=package-name" />
<link rel="alternate" href="android-app://package-name/http/url-sample.com" />
```

### Google Chrome

```html
<!-- Отключить подсказку перевода -->
<meta name="google" content="notranslate" />

<!-- Ссылка на ваше расширение chrome-->
<link
  rel="chrome-webstore-item"
  href="https://chrome.google.com/webstore/detail/APP_ID"
/>.
```

### Microsoft Internet Explorer

```html
<!-- Заставить IE 8/9/10 использовать свой последний движок рендеринга -->
<meta http-equiv="x-ua-compatible" content="ie=edge" />

<!-- Отключить автоматическое определение и форматирование возможных телефонных номеров расширением для браузера Skype Toolbar-->
<meta name="skype_toolbar" content="skype_toolbar_parser_compatible" />

<!-- Плитки Windows -->
<meta name="msapplication-config" content="/browserconfig.xml" />
```

Минимально необходимая разметка xml для `browserconfig.xml`:

```xml
<?xml version="1.0" encoding="utf-8"?>
<browserconfig>
    <msapplication>
        <tile>
            <square70x70logo src="small.png"/>
            <square150x150logo src="medium.png"/>
            <wide310x150logo src="wide.png"/>
            <square310x310logo src="large.png"/>
        </tile>
    </msapplication>
</browserconfig>
```

- 📖 [Ссылка на схему конфигурации браузера](https://msdn.microsoft.com/en-us/library/dn320426.aspx)

[⬆ вернуться к началу](#оглавление)

## CSRF атаки

```html
<!-- Токен для идентификации формы -->
<meta name="csrf-token" content="токен" />
<meta name="csrf-param" content="csrf_token" />
```

Подробнее про [CSRF-атаки](https://habr.com/ru/post/274457/)

[⬆ вернуться к началу](#оглавление)

## Подсказки HTTP клиентов

```html
<!-- Включает подсказки клиентов -->
<meta http-equiv="Accept-CH" content="DPR" />
<meta http-equiv="Accept-CH" content="DPR, Width" />
```

[Подробнее про подсказки клиентов](https://developer.mozilla.org/en-US/docs/Glossary/Client_hints)

[⬆ вернуться к началу](#оглавление)
