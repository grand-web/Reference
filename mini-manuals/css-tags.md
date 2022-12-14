## CSS теги

### Оглавление

- Оформление текста
  - [Насыщенность-шрифта](#font-weight-насыщенность-шрифта)
  - [Переносы строки](#переносы-строкиw)
  - [Оформление текста](#text-decoration-дополнительное-оформление-текста)
  - [Начертание текста](#font-style-начертание-текста)
  - [Регистр символов](#text-transform-регистр-символов)

### `font-weight`, насыщенность шрифта

Ещё один параметр шрифта, которым мы можем управлять — это **насыщенность или толщина шрифта**. Шрифт может быть жирнее или тоньше обычного начертания. Устанавливается насыщенность с помощью свойства font-weight. В качестве значения можно использовать ключевое слово или число. Самые часто встречающиеся значения:

`400` или `normal` — обычный шрифт, значение по умолчанию;

`700` или `bold` — жирный шрифт.

Например:

```html
h1 { font-weight: 400; /* то же самое что и normal */ } p { font-weight: bold;
/* то же самое что и 700 */ }
```

**На самом деле, font-weight может принимать одно из девяти числовых вариантов насыщенности:**

```
100: Thin;
200: Extra Light (Ultra Light);
300: Light;
400: Normal;
500: Medium;
600: Semi Bold (Demi Bold);
700: Bold;
800: Extra Bold (Ultra Bold);
900: Black (Heavy).
```

Все эти числовые значения задают степень толщины шрифта от самого тонкого до самого толстого.

Но в большинстве системных шрифтов всё равно есть только два варианта толщины: обычный `normal (400)` и жирный `bold (700)`. Поэтому и остальные значения свойства используются реже.

Кроме перечисленных выше числовых значений у font-weight может быть ещё два относительных значения: `bolder` и `lighter`. Эти значения делают шрифт жирнее и тоньше, чем текущее или унаследованное значение.

[⬆ вернуться к началу](#оглавление)

### Переносы строки

Свойство `white-space`, управление пробелами
Как вы уже знаете, браузер игнорирует множественные пробелы и переносы строк в HTML-коде. Изменить это поведение можно с помощью тега `<pre>`.

Однако, с помощью CSS управлять пробелами и переносами можно более гибко. За это отвечает свойство white-space, значения которого:

- `nowrap` — схлопывает лишние пробелы и отображает весь текст одной строкой без переносов;
- `pre` — сохраняет пробелы и переносы как в исходном коде аналогично тегу `<pre>`;
- `pre-wrap` — работает как значение pre, но добавляет автоматические переносы, если текст не помещается в контейнер;
- `normal` — режим по умолчанию: лишние пробелы и переносы строк схлопываются, текст переносится, пробелы в конце строк удаляются.

> 💡 На самом деле у свойства по спецификации может быть ещё два значения:  
> `break-spaces` — поведение идентично `pre-wrap`, но при схлопывании пробелов остаются нетронутыми зарезервированные пробелы, такие как пробелы в конце строки;  
> `pre-line` — как `normal`, лишние пробелы схлопываются, но строки переносятся на символе переноса строки, на `<br>` и по мере заполнения строки.

### `text-decoration`, дополнительное оформление текста

Задаёт **дополнительное оформление текста**. Значения свойства:

`underline` — подчёркивание;  
`line-through` — зачёркивание;  
`overline` — надчёркивание;  
`none` — убирает вышеперечисленные эффекты.

К тексту можно одновременно применить несколько эффектов, если перечислить значения через пробел.

> 💡 Свойство `text-decoration` — **составное**, а это значит, что его можно разложить на следующие свойства:
>
> - `text-decoration-line` — вид линии: зачёркивание, подчёркивание или надчёркивание;
> - `text-decoration-style` — стиль линии, может принимать значения:
>   - `solid` — сплошная линия;
>   - `double` — двойная линия;
>   - `dotted` — точечная линия;
>   - `dashed` — пунктирная линия;
>   - `wavy` — волнистая линия.
>   - `text-decoration-color` — цвет линии.

### `font-style`, начертание текста

Свойством можно задать **начертание текста**. Его основные значения:

`normal` — обычное начертание;  
`italic` — курсивное начертание;  
`oblique `— наклонное начертание.

> 🛠️ Если задано значение `italic`, браузер будет пытаться найти в заданном шрифте отдельное курсивное начертание символов. В некоторых шрифтах отдельный курсив предусмотрен.
> Если отдельного курсивного начертания в шрифте не предусмотрено, то браузер сделает текст наклонным, то есть сымитирует курсив. Что равноценно заданию тексту значения `font-style: oblique`.

### `text-transform`, регистр символов

С его помощью можно управлять **регистром символов**: делать буквы строчными (маленькими) или заглавными (большими). Значения свойства:

`lowercase` — все строчные;  
`uppercase` — все заглавные;  
`capitalize` — каждое слово начинается с большой буквы;  
`none` — отменяет изменение регистра.
