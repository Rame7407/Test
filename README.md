#  Триангуляция Делоне.

## Описание работы
Используется реализация алгоритма триангуляции Делоне на основе инкрементного подхода (Incremental Delaunay Triangulation). Этот алгоритм используется для разбиения множества точек на непересекающиеся треугольники таким образом, чтобы внутри окружностей, описанных вокруг каждого треугольника, не было других точек.
Общая асимптотическая сложность алгоритма инкрементной триангуляции Делоне составляет O(n log n) в среднем и O(n^2) в худшем случае где n - это количество точек.

## Реализация
Алгоритм я реализовал здесь
[Delaunay/Triangulator.cs](https://github.com/Focus1337/DelaunaySolver/blob/main/Delaunay/Triangulator.cs)
Описание работы кода:
* Проверка количества точек и инициализация структур данных:
  * Проверяется, что входной массив точек содержит как минимум 3 точки.
  * Создаются массивы и структуры данных, которые будут использоваться в ходе       алгоритма, такие как points, coords, triangles, halfedges, hullPrev, hullNext, и другие.
* Нахождение начального треугольника:
  * Находится начальная точка (i0), которая ближе всего к центру множества точек.
  * Находится вторая точка (i1), которая ближе всего к первой точке.
  * Находится третья точка (i2), образующая наименьший описывающий окружности вместе с первыми двумя точками.
* Проверка существования начального треугольника:
  * Проверяется, существует ли такой треугольник. Если не существует, выбрасывается исключение, так как алгоритм требует наличия начального треугольника.
* Ориентация начального треугольника:
  * Проверяется ориентация начального треугольника. Если он ориентирован по часовой стрелке, то меняются местами вторая и третья точки.
* Нахождение центра начального треугольника:
  * Находится центр описывающей окружности начального треугольника.
* Сортировка оставшихся точек:
  * Оставшиеся точки сортируются по расстоянию от центра описывающей окружности начального треугольника.
* Установка начальной выпуклой оболочки:
  * Устанавливается начальная выпуклая оболочка, состоящая из начального треугольника.
* Добавление оставшихся точек:
  * Для каждой оставшейся точки выполняется следующее:
    * Находится видимое ребро на текущей выпуклой оболочке.
    * Добавляется новый треугольник с этой точкой и смежными ребрами. При этом может выполняться рекурсивное переворачивание треугольников для соблюдения условия Делоне.
    * Обновляются структуры данных, представляющие выпуклую оболочку и хэш-таблицу ребер.
* Формирование массива выпуклой оболочки:
 * После обработки всех точек формируется массив hull, содержащий индексы точек выпуклой оболочки.
* Очистка лишних данных:
 * Лишние структуры данных удаляются, и массивы triangles и halfedges обрезаются до фактической длины, чтобы они содержали только треугольники, созданные во время триангуляции.

## Визуализация триангуляции
Визуализировал здесь

## Примеры работы
Триангуляция 10 точек 
Время работы:
![Example 1](Renders/Example.png "Title")
Триангуляция 10 тысяч точек
Время работы:
![Example 2](Renders/Million%20points.png "Title")
Триангуляция 1млн точек
Время работы:
![Example 2](Renders/Million%20points.png "Title")


