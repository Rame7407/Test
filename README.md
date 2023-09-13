#  Триангуляция Делоне.

## Описание работы
Используется алгоритм инкрементальной триангуляции Делоне. Этот алгоритм строит триангуляцию постепенно, добавляя каждую точку по очереди и обновляя существующую триангуляцию.

Шаги:
*Инициализация: Проверяется, что входной массив точек содержит как минимум 3 точки, так как для создания треугольника требуется как минимум 3 точки. Точки преобразуются в удобный формат координат и инициализируются необходимые структуры данных.
*Начальный треугольник: Выбирается начальный треугольник, который будет содержать первые три точки. Этот треугольник создается таким образом, чтобы он охватывал все точки с наименьшей описывающей окружностью.

*Сортировка точек: Остальные точки сортируются по расстоянию от центра начального треугольника. Это помогает определить порядок обработки точек и ускоряет алгоритм.
*Добавление точек: Для каждой оставшейся точки выполняется следующее:
*Находится видимое ребро на выпуклой оболочке текущих точек.
Добавляется новый треугольник с этой точкой и смежными ребрами. При этом выполняется рекурсивное переворачивание треугольников до выполнения условия Делоне (если это необходимо).
Обновляются структуры данных, представляющие выпуклую оболочку и хэш-таблицу ребер.
Формирование выпуклой оболочки: После обработки всех точек формируется массив, содержащий индексы точек выпуклой оболочки.
*Очистка данных: Лишние структуры данных удаляются, и массивы треугольников и половинок ребер обрезаются до фактической длины, чтобы они содержали только треугольники, созданные во время триангуляции.

Общая сложность этого алгоритма триангуляции Делоне с использованием инкрементальной постройки выпуклой оболочки составляет O(n log n), где n - количество входных точек.

## Реализация
Алгоритм я реализовал здесь
[Delaunay/Triangulator.cs](https://github.com/Focus1337/DelaunaySolver/blob/main/Delaunay/Triangulator.cs)

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


