
Пример:  
Написанное ниже правило найдёт все заголовки второго уровня в HTML и покрасит их в зелёный цвет:

```
h2 {
  color: #32a846;
}
```

## CSS-Правило
Весь CSS состоит из однотипных блоков — CSS-правил. Каждое правило состоит из как минимум одного селектора и одной пары свойство-значение.

Селектор 
При помощи селектора мы говорим браузеру, к какому именно элементу будут применяться свойства. Селектор указывает, к каким тегам применятся свойства из CSS-правила. 
Проще всего работают селекторы по тегам: они выбирают все теги с подходящим именем. 

CSS-правило состоит из нескольких обязательных элементов:

селектор {свойство: значение; }
div	   {backround: blue; }


Есть разные типы селекторов. Подробнее о них можно почитать в отдельных статьях:
универсальный селектор;
селекторы по тегу;
селектор по классу;
селектор по идентификатору;
селектор по атрибуту.

Можно написать правило сразу для нескольких селекторов, перечислив их через запятую:

.first-selector,
.next-selector {
  color: #6e4aff;
}

Селекторы можно разным образом комбинировать между собой. Подробнее в статье про комбинированные селекторы.

Сразу после селектора пишутся фигурные скобки { }. Внутри них будут перечислены свойства и значения.
Пара свойство-значение Секция статьи "Пара свойство-значение"
Свойства и их значения рассмотрим в паре, потому что они не существуют друг без друга.
Свойство указывает какой именно визуальный аспект выбранного тега будет изменяться.
А вот на то, как именно он будет изменяться, указывает значение этого свойства.
В конце строки обязательно нужно поставить точку с запятой. Иначе браузер склеит свойства и они не будут работать.

Как понять 
К селектору применятся свойства, сгруппированные в фигурных скобках. Один и тот же селектор может повторяться не один раз. За то, какие свойства в итоге применятся к элементу, отвечает каскад.

💡 Очень частая ошибка — забытая точка с запятой. Обращайте на это внимание!

https://doka.guide/css/css-rule/#kratko



.header {}
.advantages-item {}
.container {}
.footer {}


