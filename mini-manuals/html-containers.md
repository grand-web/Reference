## HTML. Потоковые контейнеры

<!-- FIXME ВСЕ СВОЙСТА Display прочитать -->

### Оглавление

[Список свойств display](#список-свойств-display)

### Свойство `display`

![](img/html-containers.png)

#### Значение `block`

```html
<div style="border:1px solid black">
  <div style="display:block; border:1px solid blue; width: 50%">Первый</div>
  <div style="display:block; border:1px solid red">Второй</div>
  <div style="display:none">Я - скрыт!</div>
  <div style="visibility:hidden">Я - невидим!</div>
</div>
```

<div style="border:1px solid black">
  <div  style="display:block; border:1px solid blue; width: 50%">Первый</div>
  <div style="display:block; border:1px solid red">Второй</div>
  <div style="display:none">Я - скрыт!</div>
  <div style="visibility:hidden">Я - невидим!</div>
</div>

Блоки прилегают друг к другу вплотную, если у них нет `margin`.

#### Значение `inline`

> ❗Ширина и высота элемента определяются по содержимому. Поменять их нельзя.

```html
<span style="border:1px solid black">
  <span style="border:1px solid blue; width:50%">Ширина</span>
  <a style="border:1px solid red">Игнорируется</a>
</span>
```

<span style="border:1px solid black">
  <span style="border:1px solid blue; width:50%">Ширина</span>
  <a style="border:1px solid red">Игнорируется</a>
</span>

Если вы присмотритесь внимательно к примеру выше, то увидите, что между внутренними `<span>` и `<a>` есть пробел. Это потому, что он есть в HTML. Если расположить элементы вплотную – его не будет.

Содержимое инлайн-элемента может переноситься на другую строку.
При этом каждая строка в смысле отображения является отдельным прямоугольником («line box»). Так что инлайн-элемент состоит из объединения прямоугольников.

```html
<div style="width:200px">
  ...<span style="background: lightgreen">
    Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля
    Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля </span
  >...
</div>
```

<div style="width:200px">
...<span style="background: lightgreen">
  Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля
  Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля Ля
</span>...
</div>

#### Значение `inline-block`

Это значение – означает элемент, который продолжает находиться в строке (`inline`), но при этом может иметь важные свойства блока.

Как и `инлайн`-элемент:  
Располагается в строке.  
Размер устанавливается по содержимому.

Во всём остальном – это `блок`:  
Элемент всегда прямоугольный.  
Работают свойства `width`/`height`.

Это значение `display` используют, чтобы отобразить в одну строку блочные элементы, в том числе разных размеров.

```html
<style>
  li {
    display: inline-block;
    list-style: none;
    border: 1px solid red;
  }
</style>

<ul style="border:1px solid black; padding:0">
  <li>Инлайн Блок<br />3 строки<br />высота/ширина явно не заданы</li>
  <li style="width:100px;height:100px">Инлайн<br />Блок 100x100</li>
  <li style="width:60px;height:60px">Инлайн<br />Блок 60x60</li>
  <li style="width:100px;height:60px">Инлайн<br />Блок 100x60</li>
  <li style="width:60px;height:100px">Инлайн<br />Блок 60x100</li>
</ul>
```

![](img/html-containers-3.png)

Свойство `vertical-align` позволяет выровнять такие элементы внутри внешнего блока (добавили в style декларацию `vertical-align: middle;`):

![](img/html-containers-4.png)

#### Значения `table`

Современные браузеры позволяют описывать таблицу любыми элементами, если поставить им соответствующие значения `display`.

Для таблицы целиком `table`, для строки – `table-row`, для ячейки – `table-cell` и т.д.

```html
<form style="display: table">
  <div style="display: table-row">
    <label style="display: table-cell">Имя:</label>
    <input style="display: table-cell" />
  </div>
  <div style="display: table-row">
    <label style="display: table-cell">Фамилия:</label>
    <input style="display: table-cell" />
  </div>
</form>
```

<form style="display: table">
  <div style="display: table-row">
    <label style="display: table-cell">Имя:</label>
    <input style="display: table-cell" />
  </div>
  <div style="display: table-row">
    <label style="display: table-cell">Фамилия:</label>
    <input style="display: table-cell" />
  </div>
</form>

Важно то, что это действительно полноценная таблица. Используются табличные алгоритмы вычисления ширины и высоты элемента,
[описанные в стандарте](https://www.w3.org/TR/CSS2/tables.html#width-layout).

> 💡 Это хорошо для **семантической вёрстки и позволяет избавиться от лишних тегов**.

С точки зрения современного CSS, обычные `<table>`, `<tr>`, `<td>` и т.д. – это просто элементы с предопределёнными значениями `display`:

```css
table {
  display: table;
}
tr {
  display: table-row;
}
thead {
  display: table-header-group;
}
tbody {
  display: table-row-group;
}
tfoot {
  display: table-footer-group;
}
col {
  display: table-column;
}
colgroup {
  display: table-column-group;
}
td,
th {
  display: table-cell;
}
caption {
  display: table-caption;
}
```

Очень подробно об алгоритмах вычисления размеров и отображении таблиц рассказывает [стандарт CSS 2.1 – Tables](https://www.w3.org/TR/CSS2/tables.html).

#### Вертикальное центрирование с table-cell

Внутри ячеек свойство vertical-align выравнивает содержимое по вертикали.
Это можно использовать для центрирования:

```html
<style>
  div {
    border: 1px solid black;
  }
</style>

<div style="height:100px; display: table-cell; vertical-align: middle">
  <div>Элемент<br />С неизвестной<br />Высотой</div>
</div>
```

<style>
  div { border:1px solid black }
</style>

<div style="height:100px; display: table-cell; vertical-align: middle">
  <div>Элемент<br>С неизвестной<br>Высотой</div>
</div>

> 💡 CSS не требует, чтобы вокруг `table-cell` была структура таблицы: `table-row` и т.п. Может быть просто такой одинокий `DIV`, это допустимо.  
> При этом он ведёт себя как ячейка `TD`, то есть подстраивается под размер содержимого и умеет вертикально центрировать его при помощи `vertical-align`.

[⬆ вернуться к началу](#оглавление)

### Свойства `display`:

```css
/* <display-outside> values */
display: block; Структурный блок, как и тег <div>.
display: inline; Строковый блок. Аналог — тег <span>.
display: run-in; поддерживает только IE.

/* <display-inside> values */
display: flow; ---?
display: flow-root;
display: table; Структурный блок. На странице ведет себя аналогично <table>.
display: flex; Структурный блок, который создает адаптивный контейнер для дочерних элементов.
display: grid; ---?
display: ruby;

/* <display-outside> plus <display-inside> values */
display: block flow;
display: inline table;
display: flex run-in;

/* <display-listitem> values */
display: list-item; Структурный блок, который отображается как элемент списка <li>
display: list-item block;
display: list-item inline;
display: list-item flow;
display: list-item flow-root;
display: list-item block flow;
display: list-item block flow-root;
display: flow list-item block;

/* <display-internal> values */
display: table-row-group; Элемент объединяет одну или несколько строк. Аналог — <tbody>.
display: table-header-group; Определяет группу строк заголовка, которая всегда отображается перед остальными строками и группами строк. Аналог — <thead>.
display: table-footer-group; Определяет группу строк заголовка, которая всегда отображается после всех остальных строк и перед любым нижним основным заголовком. Ведет себя аналогично <tfoot>.
display: table-row; Элемент является строкой ячеек. Пример — <tr>.
display: table-cell; Генерирует отдельную ячейку таблицы, на странице ведет себя аналогично <th> и <td>.
display: table-column-group; Объединяет один или несколько столбцов. Аналог — <colgroup>.
display: table-column; Описывает столбец ячеек, визуальное представление не генерируется. Аналог — <col>.
display: table-caption; Генерирует основной заголовок таблицы. На странице ведет себя аналогично <caption>.
display: ruby-base;
display: ruby-text;
display: ruby-base-container;
display: ruby-text-container;

/* <display-box> values */
Элемент не генерирует никакой контейнер, полностью удаляясь со страницы.
display: none; Не генерирует никакой контейнер, полностью удаляясь со страницы.

/* <display-legacy> values */
display: inline-block; Строковый блок.
display: inline-table; Структурный блок, который генерирует строковый блок.
display: inline-flex; Строковый блок, который создает адаптивный контейнер для дочерних элементов.
display: inline-grid;

/* Global values */
display: inherit; Наследует свойство от родительского элемента.
display: initial;
display: unset;
```

#### Колонки (`column`)

```html
div { column-count: 3; }
```

<style>
.newspaper {
  column-count: 3;
}
</style>
</head>
<body>

<div class="newspaper">
Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat. Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.
</div>

Расстояние регулирется с помощью `column-gap: 40px;`  
Линейка `column-rule: 1px solid lightblue;`
Заголовок над колонками:

```html
h2 { column-span: all; }
```
