## Markdown. Краткое руководство

### Оглавление

[Заголовки](#заголовки)  
[Выделение](#выделение)  
[Списки](#списки)  
[Ссылки](#ссылки)  
[Изображения](#изображения)  
[Якоря](#якоря)  
[Подсветка кода](#подсветка-кода)  
[Таблицы](#таблицы)  
[Цитаты](#цитаты)  
[Встроенный HTML и CSS](#встроенный-html-и-css)  
[Горизонтальная линия](#горизонтальная-линия)  
[Спойлер](#спойлер)  
[Новая строка](#новая-строка)  
[Спецсимволы](#спецсимволы)  
[Эмодзи](#эмодзи)

## Заголовки

---

Для того чтобы написать HTML заголовок в Markdown, необходимо использовать знак # (хэш). Если необходимо несколько уровней заголовков, h1 - h6, нужно изменить количество хэшей (#) перед текстом заголовка.

```md
# Заголовок 1

## Заголовок 2

### Заголовок 3

#### Заголовок 4

##### Заголовок 5 (сопоставим с **жирный**)

###### Заголовок 6 (полупрозрачный)
```

[⬆ вернуться к началу](#оглавление)

## Выделение

---

Для курсива необходимо поставить знаки \* вокруг текста. Для жирного начертания обрамим текст двумя ** звездочками, а для жирного курсива - тремя \***. Алтернативный синтаксис - использование знака \_ по тем же правилам.

```md
_Курсив_
_Курсив_
**Жирный**
**Жирный**
**_Жирный курсив_**
**_Жирный курсив_**
~~Зачеркнутый~~
```

[⬆ вернуться к началу](#оглавление)

## Списки

---

Для разметки неупорядоченных списков можно использовать \*, +, -.  
Для списка важно начинать новый абзац, и после выбранного символа обязателен пробел.
Чтоб сделать **многоуровневый список**, нужно будет сделать отступы (4 или 8 пробелов).

```md
- Элемент списка 1
- Элемент списка 2
  - Элемент второго уровня списка 1
  - Элемент второго уровня списка 2
    - Элемент третьего уровня списка 1
    - Элемент третьего уровня списка 2
    - Элемент третьего уровня списка 3
```

С нумерованными списками все еще проще:

```md
1. Первый элемент
2. Второй элемент
3. Третий элемент
```

[⬆ вернуться к началу](#оглавление)

## Ссылки

---

```md
[Обычная ссылка](https://www.google.com)

[Обычная ссылка с title](https://www.google.com 'Сайт Google')

[Ссылка со сноской][произвольный текст]

[Относительная ссылка](../blob/master/LICENSE.md)

[Для ссылок со сноской можно использовать цифры][1]

Или можно просто вставить ссылку в квадратные скобки [текст ссылки]

[произвольный текст]: https://www.mozilla.org
[1]: http://slashdot.org
[текст ссылки]: http://www.reddit.com
```

**РЕЗУЛЬТАТ**

[Обычная ссылка в строке](https://www.google.com)

[Обычная ссылка с title](https://www.google.com 'Сайт Google')

[Ссылка со сноской][произвольный текст]

[Относительная ссылка](../blob/master/LICENSE.md)

[Для ссылок со сноской можно использовать цифры][1]

Или можно просто вставить ссылку в квадратные скобки [текст ссылки]

[произвольный текст]: https://www.mozilla.org
[1]: http://slashdot.org
[текст ссылки]: http://www.reddit.com

[⬆ вернуться к началу](#оглавление)

## Изображения

---

> 💡Проще всего вставить изображение с помощью HTML тега <img\>  
> `<img src="img.png" alt="image" width="200"/>`
>
> и добавить нужные CSS атрибуты, например:  
> `style="float:right; background-color:red; width:60%; height:30%";`

По умолчанию, в markdown изображения помещаются на страницу также, как и ссылки, с одним отличием: в начале записи используется знак "!".

```md
Картинка без `alt` текста
![](//placehold.it/150x100)

Картинка с alt и title:
![Alt text](//placehold.it/150x100 'Можно задать title')

Картинки с ссылкой-сноской:
![Картинка][image1]
![Картинка][image2]
![Картинка][image3]

[image1]: //placehold.it/250x100
[image2]: //placehold.it/200x100
[image3]: //placehold.it/150x100

Картинка-ссылка:
[![Alt text](//placehold.it/150x100)](http://example.com/)
```

[⬆ вернуться к началу](#оглавление)

## Якоря

---

Якорем называется закладка с уникальным именем на определенном месте веб-страницы, предназначенная для создания перехода к ней по ссылке. Якоря удобно применять в документах большого объема, чтобы можно было быстро переходить к нужному разделу.

Пример ссылки на якорь, который перенесет в начало этого документа:

```md
[вернуться к началу](#оглавление)
```

При клике на ссылку, произойдет переход к нужному якорю, в нашем случае к заголовку второго уровня (начинающихся c ## ).  
**Пробелы** в названии якоря делаются с помощью черты "-".

> 💡 Ссылку к нужному элементу страницы можно передавать по "url + #якорь" (example.com/index.html#element) для доставки к нужному якорю (например из другой web-страницы).

> 💡 С якорями связана одна особенность работы браузера. После перехода к указанному якорю нажатие на кнопку «Назад» возвращает не на предыдущую просмотренную страницу, а к ссылке, с которой был сделан переход к якорю.  
> Получается, что для перехода к предыдущему документу надо нажать кнопку «Назад» два раза.

[⬆ вернуться к началу](#оглавление)

## Подсветка кода

---

Для оформления блока кода используется обратный апостроф ` вокруг кода. **ТРИ** символа для многострочного кода и **ОДИН** для однострочного.
Многострочный код:

````md
```
$a = 5;
$b = 3;
$c = $a + $b;
```
````

Однострочный (встраиваемый/инлайн код):

```md
`echo $c;`
```

Если внутри кода есть апостроф, то код надо обрамить двойными апострофами:

```md
`` There is a literal backtick (`) here. ``
```

> 💡 **ПОДСВЕТКА СИНТАКСИСА**
>
> Кроме того, можно (даже нужно), в многострочном коде указать синтаксис используемого языка, например: ```json, html, css, sass, js, bash, sh, shell, curl, php, mysql, postgres, sql, sqlite, dockerfile, http, md

[⬆ вернуться к началу](#оглавление)

## Таблицы

---

В чистом Маркдауне нет синтаксиса для таблиц, а в GFM есть.

```md
(Линии по бокам можно не рисовать)

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

Можно управлять выравниванием столбцов при помощи двоеточия.

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ | :-------------: | ------------: |
| col 3 is      | some wordy text |     **$1600** |
| col 2 is      |    centered     |           $12 |
| zebra stripes |    are neat     |        ~~$1~~ |

Внутри таблиц можно использовать ссылки, наклонный, жирный или зачеркнутый текст.
```

**РЕЗУЛЬТАТ**

| First Header | Second Header |
| ------------ | ------------- |
| Content Cell | Content Cell  |
| Content Cell | Content Cell  |

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ | :-------------: | ------------: |
| col 3 is      | some wordy text |     **$1600** |
| col 2 is      |    centered     |           $12 |
| zebra stripes |    are neat     |        ~~$1~~ |

[⬆ вернуться к началу](#оглавление)

## Цитаты

---

Цитаты оформляются как в эмейлах, с помощью символа \>.

```
> Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequuntur eius in labore quidem, sequi suscipit!
```

В цитаты можно помещать всё что угодно, в том числе вложенные цитаты:

> ## This is a header.
>
> 1.  This is the first list item.
> 2.  This is the second list item.
>
> > Вложенная цитата.

[⬆ вернуться к началу](#оглавление)

## Встроенный HTML и CSS

---

Mожно смешивать Markdown и HTML. Если на какие-то элементы нужно поставить классы или атрибуты, смело используем HTML:

> Выделять слова можно не только при помощи \* и \_ . Например, это <em>italic</em> и это тоже <i>italic</i>. А вот так уже <b>strong</b>, и так тоже <strong>strong</strong>. Но семантическое значение у этих тегов разное.

Можно добавить свой CSS-стиль, например в начале файла.

```md
<style>
.a1{
    color:red;
}
</style>

<p class="a1">what is DataBase</p>
```

**РЕЗУЛЬТАТ**

<style>
.a1{
    color:red;
}
</style>

<p class="a1">what is DataBase</p>

Можно и наоборот, внутри HTML-тегов использовать markdown.  
Работает **не очень** хорошо.

[⬆ вернуться к началу](#оглавление)

## Горизонтальная линия

---

В HTML мы используем тег <hr\>, в Markdown для этого служат три или более дефиса, звездочки или знака равно (-, \*, =).

```
Текст 1
---
Текст 2
*********
Текст 3
====
```

[⬆ вернуться к началу](#оглавление)

### Спойлер

Спойлер разметки — это текст, который скрывается за кнопкой с надписью, после нажатия на которую, текст становится видимым. Будте аккуратны с пробелами и отделением тела спойлера от заголовка.

<details>
  <summary>Предупреждение о спойлере</summary>

НАЧАЛО СПОЙЛЕРА. Обратите внимание, что после тега `<summary>` должен быть пробел. Вы можете написать любой markdown, который вы хотите внутри `<details>` тег ... просто убедитесь, что вы закрыли `<details>`.
КОНЕЦ СПОЙЛЕРА

</details>

```md
<details>
  <summary>Предупреждение о спойлере</summary>

НАЧАЛО СПОЙЛЕРА. Обратите внимание, что после тега `<summary>` должен быть пробел. Вы можете написать любой markdown, который вы хотите внутри `<details>` тег ... просто убедитесь, что вы закрыли `<details>`.
КОНЕЦ СПОЙЛЕРА

</details>
```

[⬆ вернуться к началу](#оглавление)

## Новая строка

---

Абзацы (параграфы) создаются при помощи **пустой строки** (Enter).
Если вокруг текста сверху и снизу есть пустые строки, то текст превращается в абзац.

Чтобы сделать только перенос строки, вместо абзаца,
нужно поставить **два пробела** в конце предыдущей строки.

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

> 💡 ⛔ ✅ ☝ ⚡ ✨ ❌ ❎ ⚠️ ❓❔❕❗ 🆕 🔜 🌀 🌈 🌎 🌟 🌿 🍀 🎉 🏳 🏴 🐋 🐳 🐦 👁 👆 👇 👉 👑 💌 💙 ❤️ 💚 💜 🖤 💬 💭 💣 💤 💫 💯 💰 💲 💻 💼 💽 💾 💿 📀 📁 📂 📃 📄 📈 📉 📊 📋 📌 📍 📎 📒 📔 📖 🔗 📝 📞 📡 📢 📣 📤 📥 📦 📧 📨 📩 🔐 🔑 🔒 🔓 🔔 🔥 🔬 🔮 🔝 🔙 ⬆ ⬇ ⬅ ➡ 🕑 🕶 🖊 🖋 🖍 🖥 🖨 🖱 🖼 🗃 🗄 🗑 🗒 🗓 🗝 🗨 🗯 🚀 🚚 🚧 🚩 🚫 🛒 🛠 🛡 🛰 🤖 🥇 🦄 ➕ ➖ 🌐 👤 💛 ⭐️ 🔧 ⚙️

[⬆ вернуться к началу](#оглавление)
