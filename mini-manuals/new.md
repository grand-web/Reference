## 🔥 Мои темплейты

## Оглавление

[Новый документ](#новый-документ)  
[Новый документ с подробным head](#новый-документ-с-подробным-head)  
[Импорт шрифтов](#импорт-шрифтов)  
[Спецсимволы](#спецсимволы)  
[Эмодзи](#эмодзи)

NAMES, ТАБЛИЦА ЭКРАНОВ, Font-face

[outlines.css.zip](content/outlines.zip)

### Новый документ

```html
<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <script defer src="main.js"></script>
    <title>Page title</title>
  </head>

  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

### Новый документ с подробным `<head>`

```html
<!DOCTYPE html>
<html lang="ru">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- <meta http-equiv="Content-Security-Policy" content="default-src 'self'" /> -->

    <style>
      /* critical styles */
    </style>

    <!-- Styles -->
    <link rel="stylesheet" href="style.css" />
    <!-- <link rel="stylesheet" href="print.css" media="print" /> -->
    <!-- <link rel="stylesheet" href="mobile.css" media="screen and (max-width: 480px)"/> -->
    <!-- <link rel="stylesheet" href="portrait.css" media="(orientation:portrait)" /> -->
    <!-- <link rel="stylesheet" href="tablet.css" media="screen and (max-width: 1080px)" /> -->

    <!--Scripts-->
    <noscript>
      <!-- js off alternarive-->
    </noscript>
    <script defer src="main.js"></script>

    <!-- App-android -->
    <meta name="theme-color" content="#4285f4" />
    <!-- <meta name="application-name" content="App Name" /> -->
    <!-- <link rel="manifest" href="manifest.webmanifest" /> -->

    <!-- Language -->
    <meta name="language" content="Russian" />
    <!-- 150 characters -->
    <meta name="description" content="" />
    <!-- 70 characters -->
    <title>Page title</title>
  </head>

  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

[CriticalCSS-generator](https://jonassebastianohlsson.com/criticalpathcssgenerator/)  
[Извлечение критического CSS-кода](https://web.dev/extract-critical-css/)

#### Предзагрузка

```html
<!-- Prefetching, preloading, prebrowsing -->
<link rel="preconnect" href="https://www.example.com/" />
<link rel="dns-prefetch" href="//example.com/" />

<link rel="prefetch" href="https://www.example.com/" />
<link rel="prerender" href="https://example.com/" />.
<link rel="preload" href="image.png" as="image" />
<link rel="modulepreload" href="super-critical-stuff.js" />
<!-- Предзагрузка модулей -->
```

[Preload, prefetch и другие теги. ](https://habr.com/ru/post/445264/)

### Open Graph (og:)

```html
<!-- 55-60 characters -->
<meta property="og:title" content="Заголовок страницы OG" />
<!-- 60-65 characters (200-twitter-card) -->
<meta property="og:description" content="Описание страницы OG" />
<!-- 200x200>600x314>1200х630 <8mb -->
<meta property="og:image" content="https://example.com/image.jpg" />
<meta property="og:url" content="https://example.com/" />
```

[Еще теги OpenGraph...](./html-head.md#facebook-open-graph-og)  
[OpenGraph Checker for Chrome](https://chrome.google.com/webstore/detail/open-graph-checker/lkjaebkedoblfeglnhbgbjbdodjdogpe)

> 💡 Можно комбинировать с twitter-card, например:  
> `<meta name="twitter:url" property="og:url" content="https://example.com">`

### Семантический `<body>`

```html
<body>
  <header>
    <h1>Это мой сайт</h1>
    <p>Он хороший</p>
    <nav>
      <ul>
        <li><a href="index.html">Эта страница</a></li>
        <li><a href="catalog.html">Другая страница</a></li>
      </ul>
    </nav>
  </header>
  <main>
    <article>
      <section>
        <h2>Первая секция</h2>
        <p>Она обо мне</p>
        <img src="images/image.png" alt="Человек и пароход" />
        <p>Но может быть и о семантике, я пока не решил.</p>
      </section>
      <section>
        <h2>Вторая секция</h2>
        <p>Она тоже обо мне</p>
      </section>
      <section>
        <h2>И третья</h2>
        <p>Вы уже должны были начать догадываться.</p>
      </section>
    </article>
  </main>
  <footer>
    <p>Сюда бы я вписал информацию об авторе и ссылки на другие сайты</p>
  </footer>
</body>
```

### Микроразметка `schema.org` (json-ld?)

https://yandex.ru/support/webmaster/schema-org/semantic-faq.html
https://yandex.ru/support/webmaster/schema-org/semantic-faq.html
https://support.google.com/webmasters/answer/3069489?hl=ru#zippy=

### PERFORMANCE

https://3perf.com/talks/web-perf-101/

### Critical Rendering Path

https://habr.com/ru/post/320430/

### Первая отрисовка контента (FCP)

https://web.dev/fcp/

### RAIL замерить производительность

https://web.dev/rail/#focus-on-the-user

### Минификация

https://css-minifier.com/  
https://codebeautify.org/minify-html

### Импорт шрифтов

```
@font-face {
  font-family: "nunito", sans-serif;
  font-weight: 400;
  font-style: normal;
  font-display: fallback; <!-- внешний вид перед загрузкой -->
}
```

[Свойство fallback](https://developer.mozilla.org/ru/docs/Web/CSS/@font-face/font-display)

### Изображения

```html
<img src="image.png" alt="text" />
```

Изображение-ссылка

```html
<a href="http://site.ru">
  <img src="image.png" alt="Описание" />
</a>
```

Размер изображения

```html
<img src="logo.png" width="200" height="100" />
```

#### Lazy-loading

```html
<img src="image.png" alt="image" loading="lazy" />
```

```html
<picture>
  <source
    srcset="my-logo-wide.webp"
    type="image/webp"
    media="(min-width: 600px)"
  />
  <source
    srcset="my-logo-wide.jpeg"
    type="image/jpeg"
    type="image/jpeg"
    media="(min-width: 600px)"
  />
  <source srcset="my-logo-narrow.webp" type="image/webp" />
  <img src="my-logo-narrow.png" alt="KOUSTAV" loading="lazy" />
</picture>
```

#### `<figure>` и `<figcaption>`

`<figure>` и `<figcaption>` Используется для группирования любых элементов, например, изображений и подписей к ним. Применяется для иллюстраций, схем, графиков, диаграмм и др.

```html
<figure>
  <img src="elephant.jpg" alt="Elephant at sunset" />
  <figcaption>An elephant at sunset</figcaption>
</figure>
```

[⬆ вернуться к началу](#оглавление)
