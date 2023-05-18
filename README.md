Теги и атрибуты SVG.

https://mpbox.ru/learn/svg/

Начало координат каждого <svg></svg> находится в левом верхнем углу.
По умолчанию в SVG используется заливка чёрного цвета.

Теги, формирующие каждое отдельное изображение, должны быть обёрнуты в Тег <svg></svg>
width, height,

<title></title> - заголовок (не влияет не отображение)
<desc></desc> - описание (не влияет на отображение)

<rect></rect> - прямоугольник или квадрат
width, height,
rx - скругление углов по горизонтали (px)
ry - скругление углов по вертикали (px)

<circle></circle> - круг
r - радиус (px)
По умолчанию центр круга и эллипса находится в начале координат тега svg,
непосредственно оборачивающего его(в левом верхнем углу),
поэтому для того, чтобы круг и эллипс не выходили за область видимости svg,
нужно применять смещения центра по осям:
cx - смещение вправо по оси абсцисс
cy - смещение вниз по оси ординат

<ellipse></ellipse> - эллипс
rx - радиус по оси абсцисс
ry - радиус по оси ординат

<polygon></polygon> - многоугольник
points - координаты вершин многоугольника по порядку соединения между собой.
Для каждой точки необходимо указать пару чисел, разделённых запятой.
Пары чисел должны разделяться символом "пробел".

<line x1="" x2=""></line> - линия
x1, y1 - координаты начальной точки отрезка
x2, y2 - координаты конечной точки отрезка
По умолчанию у линии нет обводки и цвета, поэтому она не будет отображаться.
Чтобы сделать линию видимой, нужно задать ей дополнительные атрибуты:
stroke - цвет обводки
stroke-width - толщина обводки

<polyline></polyline> - ломаная линия
points - координаты концов отрезков по порядку соединения между собой.
По умолчанию у линии нет обводки и цвета, поэтому она не будет отображаться.
Чтобы сделать линию видимой, нужно задать ей дополнительные атрибуты:
stroke - цвет обводки
stroke-width - толщина обводки
По умолчанию у polyline присутствует заливка, чтобы её отключить, необходимо указать атрибут fill="none".
fill - цвет заливки

Сложные SVG изображения удобно создавать в Adobe Illustrator.
<path></path> - путь,
определяется путем включения элемента ‘path’, для которого свойство d указывает данные пути.
Данные пути содержат инструкции moveto, lineto, curveto (как кубические, так и квадратичные Безье), arc и closepath.

<g> - объединяет все дочерние элементы в группу.
Например, для того чтобы закрасить несколько вложенных в него слоёв в одинаковый цвет,
либо группировать слои по какому-либо параметру: цвету, обводке или другим характеристикам.
Зачастую имеет уникальный id.
Так же может в себе содержать <title> и <desc> чтобы улучшить доступность для невизуальных браузеров.
В дополнение к этому, <g> обеспечивает удобство и сокращение объема кода при использовании стилей:
заданный стиль для <g> будет распространяться на все дочерние элементы.

<defs>
При использовании группировки с помощью <g> возникают проблемы:
нужно знать позицию оригинала и отталкиваться от него, а не просто указать нужные координаты;
цвета, а точнее все стили, у копий будут таким же как и у оригинала: их нельзя изменить с помощью <use>;
при использовании <g> отобразится все сгруппированные элементы. 
Заключаем сгруппированные объекты в <defs> — определяем элементы без их отображения.
Спецификация SVG рекомендует группы, которые будут повторно использоваться,
заключать в <defs>, чтобы код получился более гибким и компактным.

Элемент <use>
Часто в дизайне встречаются повторяющиеся элементы.
Например, рекламный буклет может содержать логотип компании в верхнем левом и нижнем правом углу каждой страницы.
В каком-нибудь Adobe Illustrator достаточно один раз нарисовать логотип, сгруппировать все его составляющие,
скопировать сгруппированный рисунок и вставлять его сколько угодно раз в нужные места.
Элемент <use> предоставляет аналог функции копи-паста для группы элементов, объединенных с помощью <g>.
Элемент <use> не ограничен рамками одного SVG документа:
атрибут xlink:href может сослаться на любой подходящий файл или адрес в Сети.

<symbol>
Позволяет группировать элементы другим способом.
В отличие от элемента <g>, <symbol> никогда не отображается: нет необходимости его скрывать с помощью <defs>.

<image>
Если <use> позволяет повторно использовать часть SVG файла,
то элемент <image> содержит или SVG файл целиком, или растровый файл (JPEG или PNG).
Если использоваться будет SVG файл — атрибуты x, y, width и height устанавливают окно просмотра,
в котором будет отображаться содержимое этого файла.
Если растровый файл — он будет масштабироваться чтобы соответствовать прямоугольнику, определенному атрибутами.


Методы отображения SVG на сайте

1. Непосредственное использование тега <svg></svg> со вложенными тегами в HTML-разметке сайта.
2. Использование тега <img src=""></img> с указанием атрибуте src.
3. Использование атрибута background-image:url() в стилях тега HTML:
   .image{
   display:block;
   width: 100px;
   height: 100px;
   background-image:url(01.svg);
   background-size: cover;
   background-repeat: no-repeat;
   }
   Плюсом данного метода является поддержка SVG-анимации и возможность наложения фильтров, а также использование
   спрайтов.
   Недостатки: невозможно менять стили элементов через CSS или Javascript.
4. Использование тега <object> (аналог <iframe>)
   Лучший вариант, если не требуется изменять SVG, не добавляя его в HTML-код.
   <object data="lesson3/02.svg" type="image/svg+xml">
   <img src="lesson3/02.svg">
   </object>
   Если браузер на распознает тег <object>, то он отобразит вложенный тег <img/>
   Плюсы: <object> позволяет подключать стили из внешнего CSS-файла и использовать SVG-анимации и фильтры.
   Минусы: отсутствие поддержки в старых браузерах.
5. Использование иконочных шрифтов,
   например, FontAwesome.
   Плюсы:
   картинка ведёт себя как текстовый символ и её параметры настраиваются через CSS,
   иконочные шрифты поддерживаются старыми браузерами.
   Минусы:
   ограничен функционал,
   только одноцветные картинки,
   изменения применяются ко всему изображению,
   при подключении через <link> сбой CDN приведёт к исчезновению картинок на сайте.
   Свойства изображений SVG: https://www.w3.org/TR/SVG/styling.html#InterfaceSVGStyleElement