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

Заливка и обводка

fill - заливка (цвет, градиент, по умолчанию - black)
fill-rule - как будут заливаться сложные фигуры, имеющие пересечения внутри себя:
(nonzero - в месте пересечения фигур заливка остаётся
evenodd - в месте пересечения фигур заливка исчезает)
fill-opacity - прозрачность заливки (0-1 или %)

stroke - цвет обводки (цвет, градиент, по умолчанию - none)
stroke-width - толщина обводки (px или %)
stroke-linecap - отображение концов линий
(butt(по умолчанию), round, square)
stroke-linejoin - отображение соединений линий на углах (round, bevel, mitel)
stroke-dasharray - вид пунктирной обводки (единицы или %) - длина штриха и пробела
stroke-dashoffset - смещение пунктирной обводки относительно первоначального положения (по умолчанию - 0)
stroke-opacity - непрозрачность для обводки (0-1 или %)

При необходимости создания градиента лучше воспользоваться Adobe Illustrator

<lineargradient></lineargradient> - линейный градиент
<radialGradient></radialGradient> - радиальный градиент

Изменять направление линейного градиента можно, указав положение начальной и конечной точки вектора,
указывающего его направление:
x1, y1
x2, y2
По умолчанию для линейного градиента вектор направлен слева направо:
x1="0" y1="0" x2="1" y2="0"
Чтобы поменять направление вектора на сверху вниз, нужно указать:
x1="0" y1="0" x2="0" y2="1"

Изменять направление радиального градиента можно,
указав координаты центра окружности градиента, её радиус, а также координаты фокальной точки:
cx, cy, r, fx, fy
fx и fy - fx, fy определяют фокальную точку для радиального градиента.
Градиент будет нарисован таким образом, что точка градиента 0% будет сопоставлена с (fx, fy).
Значение по умолчанию — 50%.

Каждый из тегов градиента должен содержать дочерние теги, описывающие его настройки:
<stop> - эти ноды сообщают градиенту, какой цвет он должен использовать в позициях,
определённых атрибутом offset для позиции и атрибутом stop-color.
Это может быть задано прямо в SVG или через CSS.

Для каждого из цветов, входящих в состав градиента должны быть указаны теги <stop>
атрибуты тега <stop>:
offset, % - отступ до начала перехода цвета в градиент
Точки, относительно которых рассчитывается отступ,
для всех цветов совпадают - 0%.
stop-color - цвет
stop-opacity - непрозрачность
Чтобы применить настройки градиента к нужному тегу,
нужно присвоить тегу градиента параметр id, например, id="gradient",
а в теге фигуры, к которой будет применён градиент, в параметре fill указать
fill="url(#gradient)".

Размеры SVG
viewport - область для отрисовки SVG-изображений. По умолчанию width="300" height="150".
viewBox
width
height

По умолчанию viewport элемента <svg/> имеет размеры width="300" height="150".
Если вложенные элементы будут иметь размеры, превышающие viewport, то они будут обрезаны.
Размеры элементов <svg class="image" /> можно указывать в CSS с помощью атрибута class.
Указание размеров элементов в абсолютных единицах приводит к отсутствию адаптивности.
Лучше использовать %.

Используя атрибут viewBox можно создавать адаптивные SVG-изображения.
Чтобы задать пропорции изображения,
элементу <svg/> можно указать атрибут viewBox="x0 y0 width height", где
x0 y0 - координаты начала осей координат viewBox относительно левого верхнего угла.
При этом изображение <svg/> станет адаптивным,
будет сохранять пропорции размеров width height, указанные в атрибуте viewBox,
стремясь заполнить всё доступное пространство.
Чтобы ограничить максимальные размеры изображения <svg/>,
можно воспользоваться CSS атрибутами max-width и max-height.

preserveAspectRatio
Атрибут preserveAspectRatio со значением "none" указывает,
что сохранять пропорции не нужно, что приводит к тому,
что изображение стремится заполнить всю область,
предоставленную viewBox.
Интерактивный пример: https://codepen.io/yoksel/pen/xLdQqX

Каждое окно просмотра SVG генерирует систему координат области просмотра и систему координат пользователя, изначально
идентичные.
Предоставление 'viewBox' в элементе viewport преобразует систему координат пользователя относительно системы координат
viewport, как описано в атрибуте 'viewBox'.
Дочерние элементы окна просмотра могут дополнительно изменять систему координат пользователя, например, путем указания
свойства transform.

Окна просмотра SVG могут быть вложенными.
Процентные единицы разрешаются со ссылкой на ширину и высоту ближайшего исконного окна просмотра SVG.
Таким образом, вложение видовых экранов SVG дает возможность переопределить значение процентных единиц и предоставить
новый опорный прямоугольник для «подгонки» графики относительно определенной прямоугольной области.

Ширина, высота и происхождение видовых экранов SVG устанавливаются в процессе согласования между фрагментом документа
SVG,
генерирующим окно просмотра SVG, и родительским элементом этого фрагмента (реальным или неявным). Описание этого
процесса согласования см. в разделе Создание нового окна просмотра SVG.

По умолчанию система координат вложенного окна просмотра SVG эквивалентна локальной системе координат родительского
элемента,
преобразованной в начало элемента окна просмотра SVG. Однако свойство transform элемента окна просмотра SVG изменяет
систему координат окна просмотра относительно пользовательской системы координат родительского элемента.

Абстрактно все окна просмотра SVG встроены в холст, область рисования, которая бесконечно велика во всех соответствующих
измерениях.

Системы координат
viewport space - система координат области отрисовки (начало отсчёта - левый верхний угол viewport)
user space - система координат содержимого (начало отсчёта - левый верхний угол viewBox)

По умолчанию viewport space и user space совпадают, а также совпадают используемые единицы измерения. 
В SVG могут использоваться следующие единицы измерения.
em
ex
px
pt
%
pc
cm
mm
in

При добавлении тегу svg атрибута viewBox содержимое и его система координат начинает масштабироваться и смещаться,
если в атрибуте viewBox указать значения, отличные от указанных в атрибутах width и height тега svg.

После добавления тегу svg атрибута viewBox
расположение содержимого будет рассчитываться относительно новой системы координат,
начало которой совпадает с левым верхним углом viewBox, а не от viewport (по умолчанию).

При указании положительных значений смещения осей в параметрах вложенного элемента,
оси будут смещаться вправо и вниз.
А при указаниии положительных значений смещения во viewPort - наооборот, влево и вверх.


Трансформации.
Управлять трансформацией svg можно с помощью атрибута transform.
Также возможно задавать параметры трансформации с помощью свойств CSS.

transform: (translate(x,y), scale(x,y), rotate, skewX, skewY, matrix)
translate - сдвиг по осям
scale - масштабирование по осям
rotate - поворот вокруг оси на заданный угол 
Единицы измерения угла: deg - градусы, rad - радианы, turn - повороты, grad - градианы
При использовании CSS у значения параметра должна быть указана единица измерения,
а при использовании inline стилей, наоборот, единицу измерения указывать нельзя (работать не будет).
Единицей измерения угла по умолчанию являются градусы (deg).
skewX - перекос (наклон) по оси X
matrix - настройка всех параметров трансформации в одном свойстве.
matrix() объединяет все методы 2D-преобразования в один.
Метод matrix() принимает шесть параметров, содержащих математические функции,
которые позволяют вращать, масштабировать, перемещать (перемещать) и наклонять элементы.
Параметры следующие: matrix(scaleX(), skewX(), skewY(), scaleY(), translateX(), translateY())
Удобный генератор матриц трансформации: https://angrytools.com/css-generator/transform/
