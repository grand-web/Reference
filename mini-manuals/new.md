## HTML 🔥 Мои темплейты

## Оглавление

- [1](#1)
- [спецсимволы](#спецсимволы)
- [эмодзи](#эмодзи)

NAMES, ТАБЛИЦА ЭКРАНОВ, Font-face  
Минификация - https://css-minifier.com/
https://codebeautify.org/minify-html

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

    <!-- Styles -->
    <link rel="stylesheet" href="style.css" />
    <!-- <link rel="stylesheet" href="print.css" media="print" /> -->
    <!-- <link rel="stylesheet" href="mobile.css" media="screen and (max-width: 480px)"/> -->
    <!-- <link rel="stylesheet" href="portrait.css" media="(orientation:portrait)" /> -->
    <!-- <link rel="stylesheet" href="tablet.css" media="screen and (max-width: 1080px)" /> -->

    <noscript>
      <!-- js off alternarive-->
    </noscript>
    <script defer src="main.js"></script>

    <!-- Base link-->
    <!-- <base href="https://example.com/page.html" /> -->

    <title>Page title</title>
  </head>

  <body>
    <p>Hello, world!</p>
  </body>
</html>
```

### Импорт шрифтов

```
@font-face {
  font-family: "nunito", sans-serif;
  font-weight: 400;
  font-style: normal;
  font-display: fallback; <!-- внешний вид перед загрузкой -->
}
```

[Свойство Fallback](https://developer.mozilla.org/ru/docs/Web/CSS/@font-face/font-display)

### Изображения

Lazy-loading  
`<img src="image.png" alt="image" loading="lazy" />`

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

`<figure>` и `<figcaption>` Используется для группирования любых элементов, например, изображений и подписей к ним. Применяется для иллюстраций, схем, графиков, диаграмм и др.

```html
<figure>
  <img src="elephant.jpg" alt="Elephant at sunset" />
  <figcaption>An elephant at sunset</figcaption>
</figure>
```

[⬆ вернуться к началу](#оглавление)

## Спецсимволы

---

Чтоб вставить в текст, например, знак больше >, а не выделить текст в виде цитаты, необходимо поставить перед ним **\*_обратный слеш_ \*** вот так: \\>

(_HTML_) Символы-Мнемоники — это особые строки, которые начинаются с **амперсанда** (`&`) и заканчиваются точкой с запятой (`;`). Например, знак меньше на страницу можно вставить мнемоникой `&lt`; (less than), а знак больше мнемоникой `&gt`; (greater than):

```html
&lt;ul&gt; &lt;/ul&gt;
```

Спецсимволы (который поддерживает стандарт utf-8) можно вставить по номеру `&#номер;` или имени `&имя;`):

Символы-мнемоники с кодом html:
| symbol | html |
| ------------------ | ------------- |
| ⌧ | `&#8999;` |
| 🗋 | `&#128459;` empty page |
| ⧄ | `&solb;` |
| ⊠ | `&boxtimes;` |
| ▧ | `&#9639;`|
| ⬚ |`&#11034;` |
| • | `&bull;` |
| · | `&middot;` |
| ∗ | `&lowast;` |
| ￭ | `&#65517;` |
| ▭ ▯ | `&rect;` `&#9647;` |
| □ | `&squ;` |
| < > | `&lt;` `&gt;` |
| non-breaking space | `&nbsp;` |
| ▴ ▾ ◂ ▸| `&blacktriangle;` +down/left/right|
| ☰ | `&#9776;` |
| ⋮ | `&vellip;` |
| ⨯ | `&Cross;` |  
| ‥ | `&nldr;` |
| ⋯ | `&ctdot;` |
|‘ ’ | `&lsquo;` `&rsquo;` |
| « » | `&laquo;` `&raquo;`|
| “ ”| `&ldquo;` `&rdquo;`|
| ↑ ↓ | `&uarr;` `&darr;` |
| ← → | `&larr;` `&rarr;` |

[Полный список символов-мнемоник w3](https://html.spec.whatwg.org/multipage/named-characters.html)  
[Поиск по символам](https://www.compart.com/en/unicode/html)  
[Типографические украшения](https://www.w3schools.com/charsets/ref_utf_dingbats.asp)

> ✂ ✆ ✉ ✎ ✓ ✔ ✕ ✖ ✗ ✘ ✦ ✧ ✩ ✪ ★ ☆ ✰ ✱ ✶ ❖ ❛ ❜ ❝ ❞ ❬❭ ❮❯ ❰❱ ❶ ❷ ❸ ➊ ➋ ➌ ➔ ➘ ➙ ➚ ➟ ➠ ➢ ➣ ➤ ■ □ ◼ ◻ ▪ ▫ ▲ ▵ △ ▴ ▶ ▷ ▸ ▹ ► ▻ ▼ ▽ ▾ ▿ ◀ ◁ ◂ ◃ ◄ ◅ ◆ ◇ ☂ ★ ☆ ☐ ☑ ☒ ☓ ☞ ☟ ☠ ☢ ☤ ☰ ☺ ☹ ♕ ♡ ⚐ ⚑ ⚞ ⚟ ⚠ • © ® € ₽

[⬆ вернуться к началу](#оглавление)

## Эмодзи

---

Для вставки эмодзи, можно использовать имя или номер, например `&#номер;` или `&имя;`, либо просто скопировать и вставить нужный. Размер меняется с помощью CSS-свойства, например:
`<p style="font-size:100px">&#номер;</p>`
[Подробный лист с эмодзи](https://www.w3schools.com/charsets/ref_emoji.asp)

> 💡 ⛔ ✅ ☝ ⚡ ✨ ❌ ❎ ⚠️ ❓❔❕❗ 🆕 🔜 🌀 🌈 🌎 🌟 🌿 🍀 🎉 🏳 🏴 🐋 🐳 🐦 👁 👆 👇 👉 👑 💌 💙 ❤️ 💚 💜 🖤 💬 💭 💣 💤 💫 💯 💰 💲 💻 💼 💽 💾 💿 📀 📁 📂 📃 📄 📈 📉 📊 📋 📌 📍 📎 📒 📔 📖 🔗 📝 📞 📡 📢 📣 📤 📥 📦 📧 📨 📩 🔐 🔑 🔒 🔓 🔔 🔥 🔧 🔬 🔮 🔝 🔙 ⬆ ⬇ ⬅ ➡ 🕑 🕶 🖊 🖋 🖍 🖥 🖨 🖱 🖼 🗃 🗄 🗑 🗒 🗓 🗝 🗨 🗯 🚀 🚚 🚧 🚩 🚫 🛒 🛠 🛡 🛰 🤖 🥇 🦄 ➕ ➖ 🌐 👤 💛 ⭐️

[⬆ вернуться к началу](#оглавление)
