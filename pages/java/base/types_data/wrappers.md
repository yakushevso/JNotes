##### [<-- back to Types data](../types_data/types_data.md)

## Классы-оболочки

|   Тип   | Класс-обертка |       Путь        |
|:-------:|:-------------:|:-----------------:|
|  byte   |     Byte      |  java.lang.Byte   |
|  short  |     Short     |  java.lang.Short  |
|   int   |    Integer    |  java.lang.Short  |
|  long   |     Long      |  java.lang.Long   |
|  char   |   Character   | java.lang.Integer |
|  float  |     Float     |  java.lang.Float  |
| double  |    Double     | java.lang.Double  |
| boolean |    Boolean    | java.lang.Boolean |

* Все оболочки числовых типов наследуют абстрактный класс `Number` (является частью пакета java.lang).
* Объекты классов-оберток являются неизменяемыми (Immutable).
* Переменной класса-обертки можно присваивать значение примитивного типа - автоупаковка (autoboxing).
* Переменной примитивного типа можно присваивать объект класса-обертки - автораспаковка (autounboxing).
* Автоупаковка и распаковка не работают для массивов.

Максимальное и минимальное значения:

* `MIN_VALUE` - максимальное числовое значение.
* `MAX_VALUE` - минимальное числовое значение.

Значения бесконечности:

`POSITIVE_INFINITY`

* Позитивное значение бесконечности типа double.
* Значение получается путем деления `-1,0` на `0,0`
* Строковое представление равно `-Infinity`
* Значение также является условным, и его шестнадцатеричное представление равно `FFF0000000000000`

`NEGATIVE_INFINITY`

* Отрицательное значение бесконечности типа double.
* Значение получается путем деления `1,0` на `0,0`
* Строковое представление равно `Infinity`
* Значение является условным, и его шестнадцатеричное представление равно `7FF0000000000000`

`NaN (Not-a-Number)`

* Числовое значение типа данных, которое означает «не число».
* Обычно указывает на результат недопустимых операций (разделить ноль на ноль)
* Используется для непредставимых значений (квадратный корень из -1)
* Эквивалентно значению, возвращаемому `Double.longBitsToDouble(0x7ff8000000000000L)`
* Эквивалентно значению, возвращаемому `Float.intBitsToFloat(0x7fc00000)`

### Методы реализующие подклассы класса Number

`bitCount(int i)` - возвращает количество одиночных битов в двоичном представлении дополнения до двух указанного значения int.

`reverse(int i)` - возвращает значение, полученное путем изменения порядка битов в двоичном дополнении до двух указанного значения int.

`reverseBytes(int i)` - возвращает значение, полученное путем изменения порядка байтов в дополнительном представлении до двух указанного значения int.

`isNaN(double v)` - возвращает true, если указанное число является значением Not-a-Number (NaN), и false в противном случае.

`xxxValue()` - преобразует значение объекта Number, который вызывает метод, в примитивный тип данных, возвращаемый методом.

```java
Integer x = 5;
x.byteValue(); // 5
x.doubleValue(); // 5.0
x.longValue(); // 5L
```

`compareTo()` - сравнивает объект Number, вызвавший метод, с аргументом (нельзя сравнивать два разных типа аргумента)

```java
Integer x = 5;
x.compareTo(3); // 1
x.compareTo(5); // 0
x.compareTo(8); // -1
```

`equals()` - определяет, равен ли объект Number, вызывающий метод, объекту, который передается в качестве аргумента.

```java
Integer x = 5, y = 10, z = 5;
Short a = 5;

x.equals(y); // false
x.equals(z); // true
x.equals(a); // false
```

`valueOf()` – возвращает соответствующий числовой объект, содержащий значение переданного аргумента.

```java
Integer a = Integer.valueOf(9); // 9
Double b = Double.valueOf(5); // 5.0
Float c = Float.valueOf("80"); // 80.0
Integer d = Integer.valueOf("444", 16); // 1092
```

`toString()` - используется для получения объекта String, представляющего значение объекта Number. Если метод принимает примитивный тип данных в качестве аргумента, то возвращается объект String, представляющий значение примитивного типа данных. Если метод принимает два аргумента, будет возвращено строковое представление первого аргумента в системе счисления, заданной вторым аргументом.

```java
Integer x = 5;
x.toString(); // "5"
Integer.toString(12); // "12"
```

`parseXxx()` - используется для получения примитивного типа данных определенной строки. Является статическим методом и может иметь один или два аргумента.

```java
int x = Integer.parseInt("9"); // 9
double c = Double.parseDouble("5"); // 5.0
int b = Integer.parseInt("444", 16); // 1092
```

`toXxxxString()` - возвращает строковое представление целочисленного аргумента в виде целого числа без знака в Binary/Octal/Hex формате.

```java
int i = 5;
Integer.toBinaryString(i) // 10101010
Integer.toOctalString(i)// 252
Integer.toHexString(i) // aa
```