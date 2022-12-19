## Селекторы

### Оглавление

[Селекторы по тегам](#селекторы-по-тегам)  
[Селекторы по классам](#селекторы-по-классам)  
[Вложенные селекторы](#вложенные-селекторы)  
[Соседние селекторы](#соседние-селекторы)  
[Дочерние селекторы](#дочерние-селекторы)  
[Cелекторы-атрибутов](#селекторы-атрибутов)  
[Cелектор-по-id](#селектор-по-id)  
[Таблица селекторов](#таблица-селекторов)

### Селекторы по тегам

Селекторы по именам тегов задают стили для всех элементов списка, изображений, абзацев и так далее.

```css
li {
  /* стили для элементов списка */
}
```

Если правило относится сразу к нескольким селекторам, то селекторы перечисляются через запятую:

```css
a,
img {
  /* стили для ссылок и изображений */
}
```

> 🛠 Чаще всего этот селектор применяется в самом начале файла CSS-стилей, чтобы переопределить встроенные стили браузера для некоторых тегов. Например, сразу определить стили для тегов заголовков или задать внешний вид для абзацев.

### Селекторы по классам

Можно задавать стили по классу элемента. Делается это с помощью такого селектора: `.имя_класса`. Например:

```css
.first {
  /* стили для класса first */
}
```

Синтаксис CSS позволяет выбирать элементы **одновременно по тегу и по классу** или же элемент с двумя классами сразу. Для этого селектор составляется просто одной строкой из всех желаемых «частей» **без пробелов**. В селекторе по тегу и классу первым пишется название тега, а потом идёт класс:

```html
<div class="target"></div>
```

```css
div.target {
  /* выбор всех тегов ul с классом target */
}
```

#### Перечисление

Если у элемента задано несколько классов, в HTML и в CSS-селекторе они могут идти в **разном порядке**.

```html
<span class="text green"></span>
<p class="green text"></p>
```

```css
.text.green {
  /* выбор элементов с двумя классами: text и green */
}
```

Количество классов в селекторе может быть любым:

```css
span.underlined.red.big.text {
  ...;
}
```

### Вложенные селекторы

Селектор может состоять из нескольких частей, разделённых пробелом:

```css
p strong {
  ...;
}
ul .hit {
  ...;
}
.footer .menu a {
  ...;
}
```

Такие селекторы называют контекстными или вложенными. Их используют для того, чтобы применить стили к элементу, **только если он вложен в нужный элемент.**

Читать их проще всего справа налево:

```css
p strong {
  /* выбрать все теги strong внутри тегов p */
}

ul .hit {
  /* выбрать все элементы с классом .hit внутри тегов ul */
}

.footer .menu a {
  /* выбрать все ссылки внутри элементов с классом .menu,
   которые лежат внутри элементов с классом .footer */
}
```

### Соседние селекторы

Соседние селекторы используются для расположенных рядом элементов.

Например, теги `<li>` в списке являются соседними по отношению друг к другу и вложенными в тег `<ul>`.

Соседние селекторы записываются с помощью знака `+`, например, `селектор1 + селектор2`. Стили применятся к элементу, подходящему под `селектор2`, только если сразу перед ним расположен элемент, подходящий под `селектор1`.

Пример. Есть два элемента списка:

```html
<ul>
  <li class="hit"></li>
  <li class="miss"></li>
</ul>
```

Селектор `.hit + .miss` применит стили к элементу с классом miss, так как перед ним есть элемент с классом hit.

> 💡 Селектор `.hit + li`, а также селектор `li + .miss`, или даже `li + li` тоже применит стили к элементу с классом `miss`, то есть ко второму элементу списка.

### Дочерние селекторы

Любые элементы, расположенные внутри родительского элемента называются потомками. А дочерними элементами являются ближайшие потомки. Взгляните на пример:

```html
<ul>
  <li><span>...</span></li>
  <li><span>...</span></li>
</ul>
```

По отношению к списку `<ul>` элементы `<li>` являются дочерними элементами и потомками, а `<span>` — потомки, но не дочерние элементы.

Контекстные селекторы влияют на всех потомков.

Если нужно задать стили только для дочерних элементов используется дочерний селектор, в котором используется символ `>`. Например: `ul > li` или `ul > li > span`.

> 💡 Селекторы в CSS можно очень гибко комбинировать. В частности, можно комбинировать контекстные и соседние селекторы. Например, селектор `.player-1 .hit + .miss` сработает для тега с классом miss, если сразу перед ним расположен тег с классом `hit` и оба тега расположены внутри тега с классом `player-1`.

### Селекторы атрибутов

Селекторы атрибутов позволяют выбирать элементы по любым атрибутам. Они записываются с использованием квадратных скобок: `элемент[атрибут]`. Примеры селекторов:

```css
input[checked] {
  ...;
}
input[type='text'] {
  ...;
}
```

Первый селектор выберет поля формы, у которых есть атрибут checked, второй селектор выберет поля формы, у которых атрибут `type` имеет значение `text`.

### Селектор по `id`

Для атрибута `id` существует специальный селектор. Он записывается с помощью символа #, например, #some-id.

На значение `id` распространяются те же ограничения, что и на имя класса. Также `id` должен быть уникальным на странице.

```css
#greeting {
  ...;
}
```

> 🛠 ID имеет высокую специфичность. Он будет брать верх над большинством других селекторов. В большинстве случаев предпочтительнее добавить элементу класс, чем ID. Однако, если использование ID это единственный способ нацелиться на элемент — возможно, потому вы не имеете доступа к разметке и, следовательно, возможности её редактировать — это будет работать.

### Таблица селекторов

<style>
tr:nth-child(even) {background-color: #f1f1f1!important;}
</style>

<table class="w3-table-all notranslate" ">
<tbody><tr>
<th style="width:20%">Селектор</th>
<th style="width:20%">Пример</th>
<th>Пример описания</th>
</tr>
<tr>
<td><a href="sel_class.php">.<i>class</i></a></td>
<td class="notranslate">.intro</td>
<td>Выбор всех элементов с class="intro"</td>
</tr>
<tr>
<td><a href="sel_id.php">#<i>id</i></a></td>
<td class="notranslate">#firstname</td>
<td>Выбор элемента с id="firstname"</td>
</tr> <tr>
<td><a href="sel_all.php">*</a></td>
<td class="notranslate">*</td>
<td>Выбор всех элементов</td>
</tr>
<tr>
<td><i><a href="sel_element.php">element</a></i></td>
<td class="notranslate">p</td>
<td>Выбор всех элементов &lt;p&gt;</td>
</tr>
<tr>
<td><i><a href="sel_element_comma.php">element,element</a></i></td>
<td class="notranslate">div, p</td>
<td>Выбор всех элементов &lt;div&gt; и всех элементов &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_element_element.php"><i>element</i> <i>element</i></a></td>
<td class="notranslate">div p</td>
<td>Выбор всех &lt;p&gt; элементов внутри элементов &lt;div&gt;</td>
</tr>
<tr>
<td><a href="sel_element_gt.php"><i>element</i>&gt;<i>element</i></a></td>
<td class="notranslate">div &gt; p</td>
<td>Выбор всех элементов &lt;p&gt;, в которых родительский элемент является элементом &lt;div&gt;</td>
</tr>
<tr>
<td><a href="sel_element_pluss.php"><i>element</i>+<i>element</i></a></td>
<td class="notranslate">div + p</td>
<td>Выбор всех &lt;p&gt; элементов, помещенных сразу после &lt;div&gt; элементов</td>
</tr>
<tr>
<td><a href="sel_gen_sibling.php"><i>element1</i>~<i>element2</i></a></td>
<td>p ~ ul</td>
<td>Выбор каждого элемента &lt;ul&gt;, которому предшествует элемент &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_attribute.php">[<i>attribute</i>]</a></td>
<td class="notranslate">[target]</td>
<td>Выбор всех элементов с целевым атрибутом</td>
</tr>
<tr>
<td><a href="sel_attribute_value.php">[<i>attribute</i>=<i>value</i>]</a></td>
<td class="notranslate">[target=_blank]</td>
<td>Выбор всех элементов с target="_blank"</td>
</tr>
<tr>
<td><a href="sel_attribute_value_contains.php">[<i>attribute</i>~=<i>value</i>]</a></td>
<td class="notranslate">[title~=flower]</td>
<td>Выделяет все элементы с атрибутом title, содержащим слово "flower"</td>
</tr>
<tr>
<td><a href="sel_attribute_value_lang.php">[<i>attribute</i>|=<i>value</i>]</a></td>
<td class="notranslate">[lang|=en]</td>
<td>Выбор всех элементов со значением атрибута lang, начиная с "en"</td>
</tr>
<tr>
<td><a href="sel_attr_begin.php">[<i>attribute</i>^=<i>value</i>]</a></td>
<td>a[href^="https"]</td>
<td>Выбирает каждый элемент &lt;a&gt;, значение атрибута href которого начинается с "https"</td>
</tr>
<tr>
<td><a href="sel_attr_end.php">[<i>attribute</i>$=<i>value</i>]</a></td>
<td>a[href$=".pdf"]</td>
<td>Выбирает каждый элемент &lt;a&gt;, значение атрибута href которого заканчивается ".pdf"</td>
</tr>
<tr>
<td><a href="sel_attr_contain.php">[<i>attribute</i>*=<i>value</i>]</a></td>
<td>a[href*="html5css.ru"]</td>
<td>Выбирает каждый элемент &lt;a&gt;, значение атрибута href которого содержит подстроку "html5css.ru"</td>
</tr>
<tr>
<td><a href="sel_active.php">:active</a></td>
<td class="notranslate">a:active</td>
<td>Выбор активной ссылки</td>
</tr>
<tr>
<td><a href="sel_after.php">::after</a></td>
<td class="notranslate">p::after</td>
<td>Вставка чего-либо после содержимого каждого элемента &lt; p &gt;</td>
</tr>
<tr>
<td><a href="sel_before.php">::before</a></td>
<td class="notranslate">p::before</td>
<td>Вставка чего-либо перед содержимым каждого элемента &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_checked.php">:checked</a></td>
<td>input:checked</td>
<td>Выбор каждого отмеченного &lt;input&gt; элемента</td>
</tr>
<tr>
<td><a href="sel_disabled.php">:disabled</a></td>
<td>input:disabled</td>
<td>Выбор всех отключенных элементов &lt;input&gt;</td>
</tr>
<tr>
<td><a href="sel_empty.php">:empty</a></td>
<td>p:empty</td>
<td>Выбор каждого элемента &lt;p&gt;, не имеющего дочерних элементов (включая текстовые узлы)</td>
</tr>
<tr>
<td><a href="sel_enabled.php">:enabled</a></td>
<td>input:enabled</td>
<td>Выбор всех включенных элементов &lt;input&gt;</td>
</tr>
<tr>
<td><a href="sel_firstchild.php">:first-child</a></td>
<td class="notranslate">p:first-child</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся первым дочерним элементом родительского элемента</td>
</tr>
<tr>
<td><a href="sel_firstletter.php">::first-letter</a></td>
<td class="notranslate">p::first-letter</td>
<td>Выбор первой буквы каждого элемента &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_firstline.php">::first-line</a></td>
<td class="notranslate">p::first-line</td>
<td>Выбор первой строки каждого элемента &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_first-of-type.php">:first-of-type</a></td>
<td>p:first-of-type</td>
<td>Выбор каждого элемента &lt;p&gt;, являющегося первым элементом &lt;p&gt; родительского элемента</td>
</tr>
<tr>
<td><a href="sel_focus.php">:focus</a></td>
<td class="notranslate">input:focus</td>
<td>Выбор элемента ввода, имеющего фокус</td>
</tr>
<tr>
<td><a href="sel_hover.php">:hover</a></td>
<td class="notranslate">a:hover</td>
<td>Выбор ссылок при наведении указателя мыши</td>
</tr>
<tr>
<td><a href="sel_in-range.php">:in-range</a></td>
<td class="notranslate">input:in-range</td>
<td>Выбор входных элементов со значением в указанном диапазоне</td>
</tr>
<tr>
<td><a href="sel_invalid.php">:invalid</a></td>
<td class="notranslate">input:invalid</td>
<td>Выбор всех входных элементов с недопустимым значением</td>
</tr>
<tr>
<td><a href="sel_lang.php">:lang(<i>language</i>)</a></td>
<td class="notranslate">p:lang(it)</td>
<td>Выбирает каждый элемент &lt;p&gt; с атрибутом lang, равным "it" (Итальянский)</td>
</tr>
<tr>
<td><a href="sel_last-child.php">:last-child</a></td>
<td>p:last-child</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся последним дочерним элементом родительского элемента</td>
</tr>
<tr>
<td><a href="sel_last-of-type.php">:last-of-type</a></td>
<td>p:last-of-type</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся последним &lt;p&gt; элементом его родительского элемента</td>
</tr>
<tr>
<td><a href="sel_link.php">:link</a></td>
<td class="notranslate">a:link</td>
<td>Выбор всех непосещаемых ссылок</td>
</tr>
<tr>
<td><a href="sel_not.php">:not(<i>selector</i>)</a></td>
<td>:not(p)</td>
<td>Выбор каждого элемента, не являющегося элементом &lt;p&gt;</td>
</tr>
<tr>
<td><a href="sel_nth-child.php">:nth-child(<i>n</i>)</a></td>
<td>p:nth-child(2)</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся вторым дочерним элементом родительского элемента</td>
</tr>
<tr>
<td><a href="sel_nth-last-child.php">:nth-last-child(<i>n</i>)</a></td>
<td>p:nth-last-child(2)</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся вторым дочерним элементом родительского объекта, считая от последнего дочернего элемента</td>
</tr>
<tr>
<td><a href="sel_nth-last-of-type.php">:nth-last-of-type(<i>n</i>)</a></td>
<td>p:nth-last-of-type(2)</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся вторым элементом &lt;p&gt; родительского элемента, считая от последнего дочернего элемента</td>
</tr>
<tr>
<td><a href="sel_nth-of-type.php">:nth-of-type(<i>n</i>)</a></td>
<td>p:nth-of-type(2)</td>
<td>Выбор каждого элемента &lt;p&gt;, являющегося вторым элементом &lt;p&gt; родительского элемента</td>
</tr>
<tr>
<td><a href="sel_only-of-type.php">:only-of-type</a></td>
<td>p:only-of-type</td>
<td>Выбор каждого элемента &lt;p&gt;, являющегося единственным элементом &lt;p&gt; родительского элемента</td>
</tr>
<tr>
<td><a href="sel_only-child.php">:only-child</a></td>
<td>p:only-child</td>
<td>Выбирает каждый элемент &lt;p&gt;, являющийся единственным дочерним элементом родительского элемента</td>
</tr>
<tr>
<td><a href="sel_optional.php">:optional</a></td>
<td class="notranslate">input:optional</td>
<td>Выбор входных элементов без атрибута "обязательный"</td>
</tr>
<tr>
<td><a href="sel_out-of-range.php">:out-of-range</a></td>
<td class="notranslate">input:out-of-range</td>
<td>Выбор входных элементов со значением за пределами заданного диапазона</td>
</tr>
<tr>
<td><a href="sel_read-only.php">:read-only</a></td>
<td class="notranslate">input:read-only</td>
<td>Выбор входных элементов с указанным атрибутом "ReadOnly"</td>
</tr>
<tr>
<td><a href="sel_read-write.php">:read-write</a></td>
<td class="notranslate">input:read-write</td>
<td>Выбор входных элементов с атрибутом "ReadOnly" не указан</td>
</tr>
<tr>
<td><a href="sel_required.php">:required</a></td>
<td class="notranslate">input:required</td>
<td>Выбор входных элементов с указанным атрибутом "required"</td>
</tr>
<tr>
<td><a href="sel_root.php">:root</a></td>
<td>:root</td>
<td>Выбор корневого элемента документа</td>
</tr>
<tr>
<td><a href="sel_selection.php">::selection</a></td>
<td>::selection</td>
<td>Выбор части элемента, выбранной пользователем</td>
</tr>
<tr>
<td><a href="sel_target.php">:target</a></td>
<td>#news:target </td>
<td>Выбор текущего активного элемента #news (щелчок по URL-адресу, содержащему это имя привязки)</td>
</tr>
<tr>
<td><a href="sel_valid.php">:valid</a></td>
<td class="notranslate">input:valid</td>
<td>Выбор всех входных элементов с допустимым значением</td>
</tr>
<tr>
<td><a href="sel_visited.php">:visited</a></td>
<td class="notranslate">a:visited</td>
<td>Выбор всех посещенных ссылок</td>
</tr>
</tbody></table>
