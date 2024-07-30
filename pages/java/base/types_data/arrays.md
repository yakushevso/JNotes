##### [<-- back to Types data](../types_data/types_data.md)

## Массивы

* Массив обозначается квадратными скобками.
* Класс Arrays для работы с массивами (находится в пакете java.util)

```java
int[] first;
int []first;
int first[];
int[] first, second;
```

Создание:

* Массив создается оператором `new`
* Все элементы массива инициализируются нулями.
* Размер массива фиксируется в момент создания.

```java
int[] numbers = new int[7];
String[] args = new String[5];
boolean[] bits = new boolean[0];
```

Инициализация:

* Можно перечислить значения всех элементов при создании массива.

```java
int[] numbers = new int[] {1, 2, 3, 4, 5};
boolean[] bits = new boolean[] {true, true, false};
char[] digits = {1, 2, 3, 4, 5}; // Работает только в объявлении переменной
int[] arr; arr = {1, 2, 3}; // Error: Array initializer is not allowed here
```

Индексация:

* Элементы индексируются с нуля.
* Длина массива доступна как `array.length`
* При выходе за границы массива бросается исключение `ArrayIndexOutOfBoundsException`

Многомерные массивы:

* Многомерный массив — это массив массивов.

```java
int[][] multi;
int [][]multi;
int[] multi[];
int[][] multi = new int[2][2];
int[] multi[] = new int[][] {{1, 2, 3, 4}, {1, 2, 3, 4}, {1, 2, 3, 4}} // new int[3][4]
int[][] matrix = {{1, 2}, {3, 4}}; // matrix2[1][1] -> 4
int[] row = matrix[0]; // row[0] -> 1
```

* Разрешены ступенчатые массивы.

```java
int[][] triangle = {
        {1, 2, 3, 4, 5},
        {6, 7, 8, 9},
        {10, 11, 12},
        {13, 14},
        {15}};
// triangle.length -> 5
// triangle[0].length -> 5
// triangle[4].length -> 1
```

Представление в памяти:

* Одномерный массив занимает непрерывный участок памяти.
* Двумерный массив занимает n + 1 участок в памяти, где n — первая размерность.

```java
int[][] a = new int[10][1000];
int[][] b = new int[1000][10];
```

Сравнение массивов:

* Сравнивает ссылки: `a == b`
* Сравнивает ссылки: `a.equals(b)`
* Сравнивает содержимое: `Arrays.equals(a, b)`
* Сравнивает содержимое многомерных массивов: `Arrays.deepEquals(a, b)`

Распечатка массива:

* Выводит название класса и хешкод "[I@2ce83912": `System.out.println(a)`
* Выводит содержимое: `System.out.println(Arrays.toString(a))`
* Выводит содержимое многомерных массивов: `System.out.println(Arrays.deepToString(a))`

### Методы реализующие класс Arrays

`binarySearch(int[] a, int key)` - ищет в указанном массиве целых чисел указанное значение, используя алгоритм двоичного поиска..

`binarySearch(int[] a, int fromIndex, int toIndex, int key)` - ищет указанное значение в диапазоне указанного массива целых чисел, используя алгоритм двоичного поиска.

`copyOf(int[] original, int newLength)` - копирует указанный массив, усекая или дополняя нулями (при необходимости), чтобы копия имела указанную длину.

`copyOfRange(int[] original, int from, int to)` - копирует указанный диапазон указанного массива в новый массив.

`deepEquals(Object[] a1, Object[] a2)` - возвращает true, если два указанных массива "deeply equal" друг другу.

`deepHashCode(Object[] a)` - возвращает хэш-код на основе «deep contents» указанного массива.

`deepToString(Object[] a)` - возвращает строковое представление «deep contents» указанного массива.

`equals(int[] a, int[] a2)` - возвращает true, если два указанных массива целых чисел равны друг другу.

`fill(int[] a, int val)` - присваивает определенное значение int к каждому элементу указанного целочисленного массива.

`fill(int[] a, int fromIndex, int toIndex, int val)` - присваивает указанное значение int каждому элементу указанного диапазона указанного массива целых чисел.

`hashCode(int[] a)` - возвращает хэш-код на основе содержимого указанного массива.

`parallelPrefix(int[] array, IntBinaryOperator op)` - параллельно накапливает каждый элемент заданного массива на месте, используя предоставленную функцию.

`parallelPrefix(int[] array, int fromIndex, int toIndex, IntBinaryOperator op)` - выполняет parallelPrefix(int[], IntBinaryOperator) для данного поддиапазона массива.

`parallelSetAll(int[] array, IntUnaryOperator generator)` - установите все элементы указанного массива параллельно, используя предоставленную функцию генератора для вычисления каждого элемента.

`parallelSort(int[] a)` - сортирует указанный массив в возрастающем числовом порядке.

`parallelSort(int[] a, int fromIndex, int toIndex)` - сортирует указанный диапазон массива в возрастающем числовом порядке.

`setAll(int[] array, IntUnaryOperator generator)` - установите все элементы указанного массива, используя предоставленную функцию генератора для вычисления каждого элемента.

`sort(int[] a)` - сортирует указанный массив в возрастающем числовом порядке.

`sort(int[] a, int fromIndex, int toIndex)` - сортирует указанный диапазон массива в порядке возрастания.

`spliterator(int[] array)` - возвращает Spliterator.OfInt, охватывающий весь указанный массив.

`spliterator(int[] array, int startInclusive, int endExclusive)` - возвращает Spliterator.OfInt, охватывающий указанный диапазон указанного массива.

`stream(int[] array)` - возвращает последовательный IntStream с указанным массивом в качестве источника.

`stream(int[] array, int startInclusive, int endExclusive)` - возвращает последовательный IntStream с указанным диапазоном указанного массива в качестве источника.

`toString(int[] a)` - возвращает строковое представление содержимого указанного массива.