Теги и атрибуты SVG.

Начало координат каждого <svg></svg> находится в левом верхнем углу.
По умолчанию в SVG используется заливка чёрного цвета.

Теги, формирующие каждое отдельное изображение, должны быть обёрнуты в Тег <svg></svg>
width, height,

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