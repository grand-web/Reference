<!-- TODO СРАВНИТЬ С MDN  -->

## CSS Селекторы

### Оглавление

- [Селекторы элемента](#селекторы-элемента)
- [Селекторы класса](#селекторы-класса)
- [Селектор ID](#селектор-id)
- [Селектор потомка](#селектор-потомка)
- [Универсальный селектор](#универсальный-селектор)
- [Селектор по атрибуту](#селектор-по-атрибуту)
- [Комбинированные селекторы](#комбинированные-селекторы)
- [Перечисление селекторов](#перечисление-селекторов)

> Перед тем как использовать селекторы (_select_ - выбрать), нужно понимать что их нужно использовать в связке с CSS-файлами (в примерах файл _style.css_), и все визуальные аспекты регулируются с помощью [CSS-Правил](css.md).

### Селекторы элемента

---

Селектор **элемента** иногда называется селектором **селектором тега** или селектором **типа**, поскольку он выбирает тег/элемент HTML в вашем документе.

```css
span {
  background-color: yellow;
}

strong {
  color: red;
}
```

```html
<p>
  Более эффективным способом <span>ловли льва</span> в пустыне является метод
  <strong>золотого сечения</strong> При его использовании пустыня делится на две
  неравные части, размер которых подчиняется правилу золотого сечения.
</p>
```

> ❗ Старайтесь не злоупотреблять селектором элемента из-за его очень широкого охвата. Правила, написанные для тега, будут применены ко всем таким элементам на странице вне зависимости от вложенности и заданных атрибутов. Это может привести к нежелательным последствиям.
>
> 🛠 Чаще всего этот селектор применяется в самом начале файла CSS-стилей, чтобы переопределить встроенные стили браузера для некоторых тегов. Например, сразу определить стили для тегов заголовков или задать внешний вид для абзацев.

[⬆ вернуться к началу](#оглавление)

### Селекторы класса

---

Селектор класса начинается с символа точки `.`. Он выберет в документе всё, к чему применён этот класс. В примере ниже мы создали класс с именем `.highlight`, и применили его к нескольким местам в документе. Все элементы, к которым применён класс, подсвечиваются.

```css
.article-title {
  background-color: yellow;
}
```

```html
<h2 class="article-title">Нобелевская премия по физике 2020 года</h2>
<h3 class="article-title">Шнобелевская премия 2020</h3>
```

Самое важное — **поставить точку** перед значением атрибута `class` того элемента, к которому вы хотите применить стили. Селектор без точки в начале — это селектор по тегу.

> ⚠️ Обратите внимание: селектор `.article-title `эквивалентен селектору по атрибуту `[class~="article-title"]`.

> 🛠 Селектор по классу является основным селектором для стилизации любой веб-страницы. Благодаря тому, что одному элементу можно задать несколько классов, а нескольким элементам — один и тот же класс, мы получаем очень гибкий способ стилизации страниц любой сложности.

#### Миксование Классов

У HTML-элемента может быть сколько угодно классов, в этом случае они перечисляются в атрибуте `class` **через пробел**,
например:

```html
<li class="product">Товар</li>
<li class="product hit">Товар, а ещё хит продаж</li>
<li class="product hit sale">Товар, хит продаж и со ски-и-идкой!</li>
```

Использование нескольких классов — это типовой приём, обычно его
используют так: в один класс выносят общее оформление, а в дополнительных классах описывают его модификации.

#### Нацеливание классов на отдельные элементы

В примере ниже, стиль применится ко всем заголовкам `<h2>` с атрибутом `class="article-title"`.

```css
h2.article-title {
  margin-bottom: 1.6em;
}
```

#### Нацеливание на элемент, у которого более одного класса

Вы можете применить несколько классов к элементу и нацелиться на них **по отдельности**, или выбрать элемент только если присутствуют **все классы** селектора. Это может быть полезно при создании компонентов, которые могут сочетаться на вашем сайте разными способами.

```css
.notebox {
  border: 4px solid #666;
  padding: 0.5em;
}
.notebox.warning {
  border-color: orange;
  font-weight: bold;
}
.notebox.danger {
  border-color: red;
  font-weight: bold;
}
```

```html
<div class="notebox">Это информационная заметка.</div>

<div class="notebox warning">Эта заметка показывает предупреждение.</div>

<div class="notebox danger">Эта записка показывает опасность!</div>

<div class="danger">
  Это не будет никак стилизован — у него должен быть класс notebox
</div>
```

**ДРУГОЙ ПРИМЕР**  
Стиль применится ко всем заголовкам `<h2>`, атрибут `class` которых содержит несколько значений разделённых пробелом, и среди этих значений есть `article-title` и `title-primary`.

```css
h2.article-title.title-primary {
  text-decoration: underline;
}
```

[⬆ вернуться к началу](#оглавление)

### Селектор ID

---

Селектор по id (_идентификатор_) начинается с `#`, а не с точки, но используется так же, как и селектор класса. Однако ID может быть использован единожды на странице, и к элементу может быть применён только один `id`.

```css
#first {
  color: red;
}

#last {
  border: 2px solid green;
}
```

```html
<h1 id="first">Селектор ID</h1>
<p>
  Не следует, однако забывать, что дальнейшее развитие различных форм
  деятельности позволяет оценить значение соответствующий условий активизации.
</p>

<p id="last">
  Таким образом консультация с <strong>широким активом</strong> позволяет
  выполнять важные задания по разработке существенных финансовых и
  административных условий.
</p>
```

> ⚠️ Может показаться, что неоднократное использование в документе одного и того же ID выполняет задачи стилизования, но не стоит этого делать. Результатом будет неверный код, который приведёт к многочисленным странностям в поведении.
>
> 🛠 ID имеет высокую специфичность. Он будет брать верх над большинством других селекторов. В большинстве случаев предпочтительнее добавить элементу класс, чем ID. Однако, если использование ID это единственный способ нацелиться на элемент — возможно, потому вы не имеете доступа к разметке и, следовательно, возможности её редактировать — это будет работать.
>
> 💡 Селектор `id` можно использовать для "якоря" в текcтовых файлах. В большинстве случаев в современной вёрстке используют задание якоря в HTML при помощи атрибута `id`, однако есть движки или отдельные модули, для работы которых принципиально важно чтобы он был задан через атрибут `name`.

[⬆ вернуться к началу](#оглавление)

### Селектор потомка

---

Цепочка перечисленных через пробел селекторов обозначает вложенность от родительских элементов к потомку. Это позволяет управлять стилями вложенных элементов.

> 🤖 Такие вложенные селекторы используются, если нужно задать разные стили для элемента на всей странице и для элемента внутри определённого блока.

Скажем, цвет текста в абзацах карточки новостей должен отличаться от текста на всей странице. При этом все остальные стили для абзацев одинаковые.

```html
<div class="wrapper">
  <!-- Абзац текста на странице -->
  <p class="text">Если вам скажут...</p>

  <div class="news-card">
    <h2 class="news-card__title">Все новости должны быть такими</h2>
    <!-- Абзац текста внутри новостной карточки -->
    <p class="text news-card__text">
      У пингвинов, живущих в Московском зоопарке...
    </p>
  </div>
</div>
```

Стили текста для всей страницы:

```css
.text {
  color: #ffffff;
  line-height: 1.4;
}
```

Стили для текста, вложенного в блок `.news-card`:

```css
.news-card .text {
  color: #000000;
}
```

Часто пробел не имеет особого значения. Но не в CSS. При написании стилей пробел между селекторами является _указателем взаимоотношений_ между элементами.

При чтении вложенного селектора первая часть указывает на родительский элемент, а последующие — на вложенные.

Всё просто! Берём один селектор. Берём второй селектор. Соединяем их при помощи пробела.

> 💡 Кроме пробела есть разные комбинаторы для соединения двух селекторов: `+`, `~`, `>`. Подробнее о них можно почитать в статье [комбинированные селекторы](#комбинированные-селекторы). Но чаще всего вы будете пользоваться именно пробелом.

> 🛠 Можно перечислять сколько угодно классов, спускаясь ниже и ниже по дереву вложенности элементов, но селекторы с более чем двумя составляющими сложно читать. И если нужен более сложный селектор, то это повод пересмотреть HTML-разметку и проверить её целесообразность.

[⬆ вернуться к началу](#оглавление)

### Универсальный селектор

---

Универсальный селектор обозначается звёздочкой `*`. Он выбирает **всё в документе** (или внутри родительского элемента, если он сцеплен с другим элементом). Универсальный селектор \* соответствует абсолютно любому тегу, но не включает псевдоэлементы, вроде ::before и ::after.

В следующем примере мы используем универсальный селектор, чтобы убрать внешние отступы у всех элементов. Несмотря на стилизацию по умолчанию, добавленную браузером, — он смещает заголовки и абзацы с помощью обнуления свойства отступов, — всё плотно сжато.

```css
* {
  margin: 0;
}
```

Такого рода поведение иногда можно увидеть в «таблицах сброса стилей» (пр. reset.css, normalize.css), которые вычищают всю стилизацию браузера.

> ❗ Так как универсальный селектор вызывает глобальные изменения, мы используем его в очень специфических ситуациях.

Некоторые используют универсальный селектор для изменения алгоритма расчёта размеров элементов перед началом вёрстки:

```css
* {
  box-sizing: border-box;
}
```

Учитывайте, что это CSS-правило не будет иметь влияния на псевдоэлементы. Алгоритм расчёта нужно будет менять точечно. Или дополнить селектор, упомянув в нём `::before` и `::after`:

```css
*,
::before,
::after {
  box-sizing: border-box;
}
```

#### Универсальный селектор + Комбинированные селекторы

Универсальный селектор можно использовать в [комбинированных селекторах](#комбинированные-селекторы), ограничивая его область действия.

Такое CSS-правило применит цвет текста ко всем элементам, вложенным в блок с классом `.preview`:

```css
.preview > * {
  color: green;
}
```

#### «Лоботомированная сова»

Можно использовать `*` в [смежном селекторе](#комбинированные-селекторы/#smezhnye-.element1-.element2), чтобы правило применялось только в случае, если рядом с элементом есть сосед. Например, такое CSS-правило задаст нижний отступ всем элементам при условии, что они не являются единственными детьми своего родителя:

```css
* + * {
  margin-bottom: 15em;
}
```

Такой приём в шутку называют «лоботомированная сова». Можно подробнее почитать о способах его использования в статье «[Аксиоматический CSS и лоботомированные совы](https://frontender.info/axiomatic-css-and-lobotomized-owls/)».

> 💡 Не стоит злоупотреблять универсальным селектором. Есть вероятность столкнуться с необходимостью постоянно переопределять заданные с его помощью свойства.

#### Использование универсального селектора для облегчения чтения ваших селекторов

Одно из применений универсального селектора состоит в том, чтобы облегчить чтение селекторов и сделать их более удобопонятными с точки зрения того, что они делают. Например, если мы хотим выбрать элементы-потомки элемента `<article>`, которые являются первыми дочерними элементами своего родителя, включая дочерние элементы самого `<article>`, и сделать их шрифт жирным, мы могли бы использовать псевдокласс `:first-child`, который мы будем изучать в уроке о псевдоклассах и псевдо-элементах, как селектор-потомок вместе с селектором элемента `<article>`:

```css
article :first-child {
  font-weight: bold;
}
```

Однако этот селектор можно спутать с `article:first-child`, который выберет любой элемент `<article>`, являющийся первым дочерним элементом другого элемента .

Чтобы избежать этой путаницы, мы можем добавить универсальный селектор в псевдокласс `:first-child`, чтобы было очевидно, что делает селектор. Он выбирает любой элемент, который является первым дочерним элементом элемента `<article>` или первым дочерним элементом любого потомка элемента `<article>`:

```css
article *:first-child {
  font-weight: bold;
}
```

Хотя оба делают одно и то же, удобочитаемость значительно улучшилась.

[⬆ вернуться к началу](#оглавление)

### Селектор по атрибуту

---

Element[attr]
Обозначает элемент по **названию элемента и его атрибуту**

[attr]
Обозначает элемент **по имени** атрибута attr.

[attr=value]
Обозначает элемент **с именем атрибута attr и значением** в точности совпадающим с value.

[attr~=value]
Обозначает элемент с именем атрибута attr значением которого является набор **слов разделённых пробелами, одно из которых** в точности равно значению.

[attr|=value]
Обозначает элемент с именем атрибута attr в котором используется **дефис**.

[attr^=value]
Обозначает элемент с именем атрибута attr значение которого **начинается** с "value"

[attr$=value]
Обозначает элемент с именем атрибута attr чьё значение **заканчивается** на "value"

[attr*=value]
Обозначает элемент с именем атрибута attr чьё значение содержит по крайней мере одно вхождение строки "value" как подстроки. (есть 2 варианта, с **учетом регистра и без учета**)

#### `Element[attr]` (по элементу и атрибуту)

Селектор по названию элемента и его атрибуту находит элемент на странице по наличию атрибута. Обратите внимение что пробел не нужен:

```html
<blockquote cite="А. С. Пушкин">
  Октябрь уж наступил — уж роща отряхает<br />
  Последние листы с нагих своих ветвей;
</blockquote>
```

```css
blockquote[cite] {
  background-color: #2e9aff;
}
```

#### `[attr]` (только имя атрибута или беззначный)

Селектор выберет все элементы, по имени `attr` .

```html
<button disabled>OK</button>
```

```css
[disabled] {
  background-color: red;
}
```

#### `[attr=value]` или `[attr="value"]` (точное значение)

Селектор выберет все элементы, атрибут `attr` которых в точности равен `value`.

```html
<a href="#">Пустая ссылка</a> <a href="#one">Эта ссылка не стилизуется</a>
```

```css
[href='#'] {
  color: red;
}
```

> 💡 Если в значении атрибута есть пробелы или знаки, отличные от цифр и букв, то значение нужно указывать в кавычках. В остальных случаях кавычки не обязательны.

#### `[attr~=value]` (значние приблизительно равно)

Селектор выбирает все элементы, значение атрибута `attr` это перечень слов, разделённых пробелом, и среди этих слов есть такое, чьё значение равно `value`.

```html
<blockquote cite="Александр Сергеевич Пушкин">...</blockquote>
<blockquote cite="Лев Николаевич Толстой ">...</blockquote>
```

```css
[cite~='Пушкин'] {
  border: 1px solid green;
}
```

#### `[attr|=value]` (значение с дефисом)

Селектор выберет все элементы, значение атрибута `attr` которых либо в точности равно `value`, либо начинается с `value`, за которым следует символ дефиса `-` (U+002D). Подобный вариант селектора чаще всего используется для выбора по коду языка (например `en-US` или `en-GB`).

```html
<div lang="en-us en-gb en-au en-nz">Hello World!</div>
<div lang="zh-CN">世界您好！</div>
<div lang="zh-TW">世界您好！</div>
```

Выберет первый `<div>`:

```css
[lang|='en'] {
  color: blue;
}
```

Выберет два других `<div>`:

```css
[lang|='zh'] {
  color: red;
}
```

#### `[attr^=value]` (указать начало значения)

Селектор выберет все элементы, значение атрибута `attr` которых начинается с `value`.

```html
<a href="https://secure.com/">Ссылка по протоколу HTTPS</a>
<a href="http://secure.com/">Ссылка по протоколу HTTP</a>
```

У ссылок по протоколу HTTPS справа отображается замок:

```css
[href^='https']::after {
  content: '🔐';
  margin-left: 3px;
}
```

#### `[attr$=value]`(указать конец значения)

Селектор выберет все элементы, значение атрибута `attr` которых оканчивается на `value`.

```html
<a href="https://apple.com/">Apple US</a>
<a href="https://apple.com/ru">Apple Russia</a>
<a href="https://apple.com/it">Apple Italy</a>
```

```css
a::after {
  content: '🇺🇸';
}
a[href$='/ru']::after {
  content: '🇷🇺';
}
a[href$='/it']::after {
  content: '🇮🇹';
}
```

#### `[attr*=value]` (любое слово внутри значения)

Селектор выберет все элементы, атрибут `attr` которых содержит в себе значение `value`.

```html
<img src="/img/myadvertisingbanner.png" />
<img src="/img/other-advert-banner.png" />
<img src="/img/Advert-image.png" />
```

Спрячет две первых рекламных картинки. Оба изображения в атрибуте `src` содержат подстроку `advert`.

```css
img[src*='advert'] {
  display: none;
}
```

> ❗️Третья картинка не спрячется, потому что не совпал регистр символов. Advert и advert — это разные значения с точки зрения браузера.

#### `[attr operator value i]`(любое слово игнорируя регистр)

Если добавить в скобки после значения атрибута `i` или `I`, то браузер будет игнорировать регистр символов.

```html
<img src="/img/myadvertisingbanner.png" />
<img src="/img/other-advert-banner.png" />
<img src="/img/Advert-image.png" />
```

Теперь будут спрятаны все три картинки

```css
img[src*='advert' i] {
  display: none;
}
```

**ДОПОЛНИТЕЛЬНО**

> 🛠 При помощи селектора по атрибуту круто стилизовать ссылки, основываясь на значении атрибута href. Можно визуально разделять ссылки, ведущие на соседние страницы сайта, и ссылки, ведущие на другие сайты:

```html
<a href="http://mysite.ru/about">О нас</a>
<a href="http://mysite.ru/delivery">Доставка</a>
<a href="http://mysite.ru/contacts">Контакты</a>
<a href="http://medium.com/mysite-blog">Мы на Medium</a>
```

```css
/* Все ссылки будут с иконкой стрелочки: */

[href^='http']::after {
  content: '⬆';
}

/* Внутренние ссылки — без иконок: */

[href*='/mysite.ru/']::after {
  display: none;
}
```

[⬆ вернуться к началу](#оглавление)

### Комбинированные селекторы

<!-- FIXME ПРОЧИТАТЬ ВСЕ НИЖЕ -->

---

#### Группировка: `.element1, .element2`

Можно перечислить все селекторы через запятую и написать всего одно CSS-правило:

```css
h1,
h2,
h3 {
  font-weight: bold;
}
```

Селекторы просто записываются в произвольном порядке через запятую:

```css
.selector1,
code,
#id,
[attr='value'] {
  color: red;
}
```

Если вы перечисляете селекторы через запятую, то правила будут применяться к каждой из групп:

```css
.heading span,
.block,
.wrapper {
  color: red;
}
```

В этом примере свойство применится для трёх типов селекторов:

- Для всех `<span>` внутри класса `.heading` (на любом уровне вложенности);
- для всех элементов с классом `.block`;
- для всех элементов с классом `.wrapper`.

#### Объединение: `.class1.class2`

```css
.selector.selector_modificator {
  color: red;
}
```

Этот приём применим только для классов и атрибутов, потому что только их может быть больше одного. Селекторы записываются слитно. Стили будут применены только к тому элементу, который содержит все перечисленные селекторы.
Такое «склеивание» объединяет селекторы в одно правило.

#### Потомки: `.element1 .element2`

```css
article h3 {
  color: red;
}
```

Селекторы записываются последовательно через пробел.
Последовательность селекторов отражает вложенность — каждый следующий селектор должен обязательно находиться на каком-то уровне вложенности в предыдущий селектор.

#### Непосредственно вложенные: `.element1 > .element2`

Селекторы разделяются знаком `>`.
Последовательность селекторов отражает непосредственную вложенность — селектор справа от оператора должен быть прямым потомком селектора из левой части:

```css
article > h3 {
  color: red;
}
```

К `h3.article__heading` стили для `article > h3` не применятся, т. к. прямой потомок [`<article>`](/html/article/) — `div.article__header`, а не [`<h3>`](/html/h1-h6/):

```html
<article class="article">
  <div class="article__header">
    <h3 class="article__heading">Заголовок</h3>
  </div>
</article>
```

В этом примере стили к заголовку применятся, потому что `<h3>` является прямым потомком `<article>`:

```html
<article class="article">
  <h3 class="article__heading">Заголовок</h3>
</article>
```

И тут тоже всё в порядке — `<h3>` по-прежнему является прямым потомком `<article>`, потому что располагается на ближайшем уровне вложенности, хоть и следует после `div.article__header`:

```html
<article class="article">
  <div class="article__header">…</div>
  <h3 class="article__heading">Заголовок</h3>
</article>
```

> 💡 Такая комбинация удобна, чтобы выбрать элемент, основываясь на его точном расположении в структуре документа.

#### Смежные: `.element1 + .element2`

Селекторы объединяются знаком `+`.
Элемент справа от `+` должен следовать в HTML сразу за элементом слева. Проще говоря, правый элемент должен быть _соседом_ левого элемента, чтобы смежный селектор сработал.

Код из примера применится только к такому [`<input>`](/html/input/), который стоит сразу после [`<label>`](/html/label/):

```css
label + input {
  color: red;
}
```

К этому **не применится**, т. к. перед `<input>` идёт [`<p>`](/html/p/):

```html
<label></label>
<p>…</p>
<input />
```

При такой разметке стиль применится только к первому `<input>`, но не ко второму:

```html
<label>Лейбл</label>
<input />
<input />
```

И тут правило **не сработает**. [`<label>`](/html/label/) и `<input>` — на разных уровнях вложенности:

```html
<label>Лейбл</label>
<div>
  <input />
</div>
```

#### Последующие: `.element1 ~ .element2`

```css
.star:hover ~ .star {
  color: red;
}
```

Селекторы объединяются с помощью символа `~` (тильда).

Правило применится ко всем блокам, подходящим под правый селектор, при учёте, что они являются соседями блоков из селектора слева от `~`. При этом оба селектора должны иметь одного родителя и находиться на одном уровне вложенности. В HTML правый селектор должен идти после левого селектора.

> 💡 Лучше записывать селекторы по одному на строчку — так их легче читать и редактировать.

**ДОПОЛНИТЕЛЬНО**

> 🛠 Объединение увеличивает специфичность правила, поэтому это может быть удобно для переопределения свойств без `!important`:

Код ниже нельзя редактировать по каким-то причинам:

```html
.class1 { color: red; }
```

Увеличим специфичность, чтобы переопределить правило, описанное в нередактируемой части и потому имеющее больший вес:

```css
.class1.class2 {
  color: green;
}

.class1 {
  color: red;
}
```

В итоге текст в блоке, имеющем сразу и класс `.class1` и класс `.class2`, будет зелёного цвета.

> 🛠 Получается, что даже невинный пробел уже имеет значение при выборе селектора на любом уровне вложенности.

**ЕЩЕ ПРИМЕР**

Независимо от уровня вложенности селектор article h3 «найдёт» `<h3>` с текстом «Очень вложенный заголовок» и любые другие `<h3>`, которые располагаются внутри `<article>`:

```html
<article>
  <div>
    <div>
      <div>
        <div>
          <div>
            <div>
              <div>
                <div>
                  <div>
                    <h3>Очень вложенный заголовок</h3>
                  </div>
                </div>
              </div>
              <h3>Заголовок</h3>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</article>
```

**ДРУГОЙ ПРИМЕР**

> 🛠 С помощью смежного комбинатора удобно выбирать группу одинаковых элементов по принципу «все, кроме первого» — например, чтобы задать отступ.

К первому `<li>` стили не применятся, поскольку перед ним нет другого `<li>`:

```html
<ul>
  <li>Первый пункт</li>
  <li>Второй пункт</li>
  <li>Третий пункт</li>
  <li>Четвёртый пункт</li>
</ul>
```

```css
li + li {
  margin-top: 1em;
}
```

<!-- TODO Создать свой html темплейт для звездного рейтинга -->

Классический пример — вёрстка «звёздного» рейтинга. Для начала опишем структуру:

```html
<div class="rating">
  <button>★</button>
  <button>★</button>
  <button>★</button>
  <button>★</button>
  <button>★</button>
</div>
```

И стили:

```css
button {
  border: none;
  background-color: transparent;
  font-size: 5em;
}

button:hover,
button:focus,
button:hover ~ button,
button:focus ~ button {
  color: #f498ad;
}
```

Но сейчас при наведении курсора будут выделяться все элементы после (то есть справа).
Чтобы это исправить, мы изменим порядок следования элементов с помощью CSS-свойства `direction: rtl`. (_RTL Right-to-left_- это языки справа налево, например китайский)

Добавим это свойство родителю звёздочек `.rating` (добавить правило выше `button`):

```css
.rating {
  direction: rtl;
}
```

[⬆ вернуться к началу](#оглавление)

### Перечисление селекторов

---

При помощи перечисления нескольких селекторов через запятую можно избежать дублирования кода.

> 🤖 Если у нескольких элементов есть определённые повторяющиеся стили, то вполне допустимо вынести эти стили в отдельный блок и в качестве селектора указать несколько классов (или тегов, или идентификаторов), перечислив их через запятую.

Представим, что у всех заголовков на странице одинаковый цвет текста, высота строки и есть декоративный элемент в виде подчёркивания.

```html
<div class="wrapper">
  <h1 class="main-title">Только хорошие новости</h1>
  <h2 class="title">Учёные научились выращивать зубы</h2>
  <p class="text">
    Группа специалистов впервые сумела вырастить настоящий зуб ...
  </p>
</div>
```

Задаём общие стили для заголовков. Ниже создаём одинаковые декоративные подчёркивания при помощи псевдоэлементов.

```css
.main-title,
.title {
  position: relative;
  display: inline-block;
  color: #ffffff;
  font-weight: 500;
}

.main-title::before,
.title::before {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 100%;
  height: 3px;
  border-radius: 3px;
  background-color: #ffffff;
  z-index: -1;
}
```

> 🤖 Перечисляемые через запятую селекторы могут быть никак не связаны между собой родственными связями, могут находиться в разных частях разметки или вообще на разных страницах. Стили, описанные внутри фигурных скобок, будут в равной степени применены и к первому, и ко второму, и ко всем последующим селекторам.

Указывается один селектор, после него ставится запятая, через пробел указывается второй селектор и так далее.
Для удобства чтения можно переносить каждый новый селектор на новую строку, но технически это не обязательно.

Селекторами может быть не только селектор по классу, но и селектор по тегу или по идентификатору, или даже их комбинация.

> 💡 Если стили у перечисляемых блоков не отличаются ничем, то это причина пересмотреть разметку и задать одинаковым по стилям элементам одинаковый класс.

> 💡 Если перечисляете через запятую составные селекторы, то нужно указывать их полностью.

**ДОПОЛНИТЕЛЬНО**

🛠 Начинающие разработчики часто допускают ошибку при перечислении селекторов: по их логике первая часть составного селектора не требует повторения и её можно указать один раз в начале, а затем перечислить через запятую несколько «вторых» частей составного селектора.

Вложенным селектор считается только в первой строке, остальные классы отдельные,
сами по себе.

Вот так **неверно**:

```css
.parent-class .child-class,
.another-class,
.one-another-class {
  /* Стили */
}
```

А вот так **верно!** Все три перечисленных селектора являются вложенными:

```css
.parent-class .child-class,
.parent-class .another-class,
.parent-class .one-another-class {
/_ Стили _/
}
```

> 💡По факту, перечисление через запятую — просто удобный способ сокращения кода, что вписывается в рамки принципа DRY.
>
> 🛠 Не злоупотребляйте перечислением селекторов через запятую. Особенно составных. Если в стилях слишком много перечислений селекторов, присмотритесь к одной из методологий написания CSS — например, БЭМ.

[⬆ вернуться к началу](#оглавление)