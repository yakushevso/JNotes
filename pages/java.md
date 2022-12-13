##### [<-- back to README](/README.md)

## Java

### Общее

#### JDK, JRE и JVM


* JDK (Java Development Kit) - набор программ для разработки. Включает в себя JRE, загрузчик кода java, компилятор javac, архиватор jar, генератор документации javadoc и другие утилиты.
* JRE (Java Runtime Environment) - окружение, необходимое для запуска Java-программ. Включает в себя JVM, стандартную библиотеку (пакеты lang, util, пакеты для работы с различными форматами, базами данных, пользовательским интерфейсом и другие пакеты).
* JVM (Java Virtual Machine) - виртуальная машина отвечает за выполнение байт-кода Java (.class).

#### Сборка, исполнение и архивация


Компиляция кода:

`javac HelloWorld.java`

* На выходе получаем файл HelloWorld.class

Запуск HelloWorld.class:

`java -cp . HelloWorld`  
 * Ключ `-cp` сокращение от `-classpath` указывает компилятору, где искать исходные файлы.

Компиляция кода с созданием каталогов:

`javac -d bin src/HelloWorld.java`  

На выходе получаем каталоги:  
* Исходный файл - `src/HelloWorld.java`  
* Скомпилированный файл - `bin/HelloWorld.class`

Запуск bin/HelloWorld.class из каталога:

`java -cp ./bin HelloWorld`

Архивация файлов (JAR - Java Archive):

`jar -cf jar-файл входной-файл(ы)`  
* Ключ `c` показывает, что необходимо создать (create) JAR-файл.
* Ключ `f` показывает, что необходимо направить вывод в файл, а не в стандартный поток вывода.
* `jar-файл` - название выходного JAR-файла с расширением `.jar`
* `входной-файл(ы)` - список файлов через пробел, которые необходимо поместить в JAR-файл.
* Команда `jar` автоматически создает файл `MANIFEST.MF` и помещает в каталог `META-INF`

Кроме JAR, также существуют другие архивы, связанные с Java:

* WAR (**W**eb **A**pplication A**r**chive) - содержит в себе приложение для веба.
* EAR (**E**nterprise **A**pplication A**r**chive) - содержит в себе энтерпрайз приложение (обычно из нескольких модулей).
* APK (**A**ndroid A**p**plication Pac**k**age) - содержит в себе приложение для Android.

#### Ключевые слова Java

Список ключевых слов:

* Примитивные типы: `byte`,`short`,`int`,`long`,`float`,`double`,`char`,`boolean`
* Управление потоком: `if`,`else`,`for`,`do`,`while`,`switch`,`case`,`default`,`break`,`continue`,`return`
* Обработка исключений: `try`,`catch`,`finally`,`throw`,`throws`,`assert`
* Модификаторы: `public`,`private`,`protected`,`final`,`static`,`native`,`abstract`,`synchronized`,`transient`,`volatile`,`strictfp`
* Связанные с классом: `class`,`interface`,`package`,`extends`,`implements`,`import`
* Связанный с объектом: `new`,`instanceof`,`super`,`this`
* Литералы: `true`,`false`,`null`
* Другие: `void`,`enum`
* Не используется: `goto`,`const`

### Типы данных

#### Целочисленные типы

Тип|Описание|Размер (бит)|Диапазон
:---:|---|:---:|---
byte | Наименьшие целые числа | 8 бит | от -128 до 127
short | Короткие целые числа | 16 бит | от -32768 до 32767
char | Символы | 16 бит | беззнаковое целое число, символ UTF-16 (буквы и цифры)
int | Целые числа | 32 бит | от -2147483648 до 2147483647
long | Длинные дробные числа | 64 бит | от -9223372036854775808L до 9223372036854775807L

Литералы:

* Десятичное число (_Decimal_): `123`
* Восьмеричное число (_Octal_): `0123`
* Шестнадцатеричное число (_Hex_): `0x123`
* Двоичное число (_Binary_): `0b101` (с Java 7)
* С подчеркиванием: `123_456_789` (с Java 7)
* С суффиксом L для long: `123456789L`

Класс-обертка для byte, short, int, long:

* MIN_VALUE
* MAX_VALUE
* toString(typename)
* parseTypename(String)
* bitCount(typename)
* reverse(typename)
* reverseBytes(typename)

#### Char (Unicode)

Литераллы:
* символы в одинарных кавычках: `'a'`
* шеснадцатиричный код символа: `'\u78bc'`
* спецпоследовательности: `'\t'`, `'\n'`, `'\r'`, `'\''`, `'\\'`

Класс-обертка для char:

* char toLowerCase(char)
* char toUpperCase(char)
* boolean isLowerCase(char)
* boolean isUpperCase(char)
* boolean isDigit(char)
* boolean isLetter(char)
* boolean isHighSurrogate(char)
* boolean isLowSurrogate(char)

Некоторые символы представляются двумя char'ами - суррогатной парой.

Таблица ASCII:

![tableAscii](/img/tableAscii.jpg)

![ascii](/img/ascii.png)

#### Типы с плавающей точкой

Тип|Описание|Размер (бит)|Диапазон
:---:|---|:---:|---
float | Длинные дробные числа | 32 бит | от 1.4e-45f до 3.4e+38f
double | Дробные числа двойной точности | 64 бит | от 4.9e-324 до 1.7e+308

* Стандарт [IEEE754](https://ru.wikipedia.org/wiki/IEEE_754-2008)
* Побитовые операции не поддерживаются.

Литералы:

* Обычная запись: `-1.234`
* Экспоненциальная запись: `-123.4e-2` (−123.4 * 10−2)
* Шестнадцатеричная запись: `0xFFFFpFF` (FFFF * 2 FF )
* С суффиксом типа: `38f`, `3e19d`, `123.4e-2f`, `444.444d`

Особые случаи:

* Деление положительного числа на 0 дает +∞
* Деление отрицательного числа на 0 дает −∞
* Деление 0 на 0 дает NaN
* Переполнение дает +∞ или −∞, в зависимости от направления.
* NaN != NaN

strictfp:

* Java использует FPU для вычислений с плавающей точкой, но регистры  FPU могут быть шире 64 бит, в результате вычисления могут отличаться.
* Модификатор strictfp включает режим строгой совместимости, результаты будут идентичны на любом процессоре.

Класс-обертка для float, double:

* MIN_VALUE
* MAX_VALUE
* POSITIVE_INFINITY
* NEGATIVE_INFINITY
* NaN
* boolean isNaN(typename)
* toString(typename)
* parseTypename(String)

#### Логический тип

Тип|Описание|Размер (бит)|Диапазон
:---:|---|:---:|---
boolean	| Булевы выражения | 8 (в массивах) / 32 (не в массивах) | true (истина) или false (ложь)

#### Ссылочные

* Наследуют `java.lang.Object`
* Ссылка может принимать значение `null`

#### String

java.lang.String

* Класс реализует интерфейсы Serializable и CharSequence.
* Поскольку он входит в пакет java.lang, его не нужно импортировать.
* Класс String в Java — это final класс, который не может иметь потомков.
* Класс String — immutable класс, то есть его объекты не могут быть изменены после создания.
* Любые операции над объектом String, результатом которых должен быть объект класса String, приведут к созданию нового объекта.
* Благодаря своей неизменности, объекты класса String являются потокобезопасными и могут быть использованы в многопоточной среде.
* Каждый объект в Java может быть преобразован в строку через метод toString, унаследованный всеми Java-классами от класса Object.
* Строка — это не char[], хотя есть способы конвертации.
* Никаких нулевых символов в конце, длина хранится отдельно.

Строковые литералы:

```java
String zeros = "\u0000 \u0000";
String hello = "Hello";
String specialChars = "\r \n \t \" \\";
String unicodeEscapes = "\u0101 \u2134 \u03ff";
```

Создание из массива символов с помощью конструктора:

```java
char[] charArray = {’a’, ’b’, ’c’, ’d’};
String string = new String (charArray); // abcd
String string = new String (charArray, 0, 2); // ab
```

Доступ к содержимому строки:

```java
int length()
char charAt(int index)
char[] toCharArray()
String substring(int beginIndex)
String substring(int beginIndex, int endIndex)
```

Конкатенация строк:

```java
String helloWorld = "Hello " + "World!";
```

java.lang.StringBuilder:

```java
StringBuilder buf = new StringBuilder();
buf.append ("Hello ");
buf.append ("World!");
String result = buf.toString();
```

Сравнение строк:

* Оператор `==` сравнивает ссылки, а не содержимое строки.

```java
boolean equals(Object anObject)
boolean equalsIgnoreCase(String anotherString)
int compareTo(String anotherString)
int compareToIgnoreCase(String anotherString)
```

#### Arrays

* Массив обозначается квадратными скобками.

```java
int[] first;
int first[];
int[] first, second;
int first[], second;
```

Создание:

* Массив создается оператором `new`
* Все элементы массива инициализируются нулями.
* Размер массива фиксируется в момент создания.

```java
int[] numbers = new int[100];
String[] args = new String[1];
boolean[] bits = new boolean[0];
```

Инициализация:

* Можно перечислить значения всех элементов при создании массива.

```java
int[] numbers = new int[] {1, 2, 3, 4, 5};
boolean[] bits = new boolean[] {true, true, false};
// это работает только в объявлении переменной
char[] digits = {
        ’0’, ’1’, ’2’, ’3’, ’4’,
        ’5’, ’6’, ’7’, ’8’, ’9’};
```

Индексация:

* Элементы индексируются с нуля.
* Длина массива доступна как `array.length`
* При выходе за границы массива бросается исключение `ArrayIndexOutOfBoundsException`

Многомерные массивы:

* Многомерный массив — это массив массивов.

```java
int[][] matrix0 ;
int[][] matrix1 = new int[2][2];
int[][] matrix2 = {{1, 2}, {3, 4}};
int[] row = matrix2[0]
// matrix2[1][1] -> 4
// row[0] -> 1
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

Varargs:

* Специальный синтаксис для массива аргументов (Поддерживается с Java 5).

```java
int max(int[] numbers);
// usage: max (new int[] {1, 2, 3, 4});
int max(int... numbers);
// usage: max(1, 2, 3, 4);
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

java.util.Arrays:

* copyOf, copyOfRange
* fill
* sort
* binarySearch
* java.lang.System.arraycopy

#### Классы-оболочки

Тип|Класс-обертка|Путь
:---:|:---:|:---:
byte | Byte | java.lang.Byte
short | Short | java.lang.Short
int | Integer | java.lang.Short
long | Long | java.lang.Long
char | Character | java.lang.Integer
float | Float | java.lang.Float
double | Double | java.lang.Double
boolean | Boolean | java.lang.Boolean

* Все оболочки числовых типов наследуют абстрактный класс Number.
* Объекты классов-оберток являются неизменяемыми (Immutable).
* Переменной класса-обертки можно присваивать значение примитивного типа - автоупаковка (autoboxing).
* Переменной примитивного типа можно присваивать объект класса-обертки - автораспаковка (autounboxing).
* Автоупаковка и распаковка не работают для массивов.

Служебные методы:

valueOf() – возвращает соответствующий числовой объект, содержащий значение переданного аргумента.

```java
Integer a = Integer.valueOf(9); // 9
Double b = Double.valueOf(5); // 5.0
Float c = Float.valueOf("80"); // 80.0
Integer d = Integer.valueOf("444", 16); // 1092
```

xxxValue() - преобразует значение объекта Number, который вызывает метод, в примитивный тип данных, возвращаемый методом.

```java
Integer x = 5;
x.byteValue(); // 5
x.doubleValue(); // 5.0
x.longValue(); // 5L
```

parseXxx() - используется для получения примитивного типа данных определенной строки. Является статическим методом и может иметь один или два аргумента.

```java
int x = Integer.parseInt("9"); // 9
double c = Double.parseDouble("5"); // 5.0
int b = Integer.parseInt("444", 16); // 1092
```

toString() - используется для получения объекта String, представляющего значение объекта Number. Если метод принимает примитивный тип данных в качестве аргумента, то возвращается объект String, представляющий значение примитивного типа данных. Если метод принимает два аргумента, будет возвращено строковое представление первого аргумента в системе счисления, заданной вторым аргументом.

```java
Integer x = 5;
x.toString(); // "5"
Integer.toString(12); // "12"
```

toXxxxString() - возвращает строковое представление целочисленного аргумента в виде целого числа без знака в Binary/Octal/Hex формате.

```java
int i = 5;
Integer.toBinaryString(i) // 10101010
Integer.toOctalString(i)// 252
Integer.toHexString(i) // aa
```

#### Приведение типов

![cast](/img/cast.png)

Автоматические преобразования (с потерей точности):  
int --> float, long --> float и long --> double

```java
int a = 2147483647;
float b = a; // от типа int к типу float
System.out.println(b); // 2.14748365E9
```

Явные преобразования (с потерей точности):

```java
int a = 258;
byte b = (byte) a;
System.out.println(b); // 2
```

#### Арифметические операции

Оператор|Описание
:---:|---
\+ | сложение
\- | вычитание
\* | умножение
/ | деление целочисленное
% | остаток / деление по модулю `9 % 4 = 1`
\+= | сложение с присваиванием
\-= | вычитание с присваиванием
\*= | умножение с присваиванием
/= | деление с присваиванием
%= | деление по модулю с присваиванием
\++ | инкремент
\-- | декремент

* Деление на ноль — выбрасывается исключение `ArithmeticException`
* Переполнение не является исключением, лишние старшие биты выкидываются.

#### Оператор инкремент / декремент

* Оператор предварительного приращения возвращает значение после приращения. Оператор постинкремента возвращает значение до инкремента.

```java
int i = 25;
int j = ++i; // i увеличивается до 26, присваивается j
System.out.println(i + " " + j); //26 26
        
i = 25;
j = i++; // i значение (25) присваивается j, затем увеличивается до 26
System.out.println(i + " " + j); // 26 25
```

```java
i = 25;
j = --i; // i уменьшается до 24, присваивается j
System.out.println(i + " " + j);//24 24

i = 25;
j = i--; // i значение (25) присваивается j, затем уменьшается до 24
System.out.println(i + " " + j); // 24 25
```

### Math

java.lang.Math

* константы: E, PI
* тригонометрия: sin, cos
* степени: sqrt, pow, exp
* min, max

### Побитовые операции

Оператор | Описание
:---:|---
~ | Побитовый унарный оператор NOT
& | Побитовый AND
&= | Побитовый AND с присваиванием
&#124; | Побитовый OR
&#124;= | Побитовый OR с присваиванием
^ | Побитовый исключающее OR
^= | Побитовый исключающее OR с присваиванием
\>> | Сдвиг вправо
\>>= | Сдвиг вправо с присваиванием
\>>> | Сдвиг вправо с заполнением нулями
<< | Сдвиг влево
<<= | Сдвиг влево с присваиванием
\>>>= | Сдвиг вправо с заполнением нулями с присваиванием

`>>` - арифметический сдвиг  
`>>>` - логический сдвиг

A | B | A &#124; B | A & B | A ^ B | ~A
:---:|:---:|:---:|:---:|:---:|:---:
0 | 0 | 0 | 0 | 0 | 1
1 | 0 | 1 | 0 | 1 | 0
0 | 1 | 1 | 0 | 1 | 1
1 | 1 | 1 | 1 | 0 | 0

### Операторы сравнения (логические)

Оператор | Пример использования | Возвращает значение "истинно", если...
:---:|:---:|---
\> | a > b | а больше b
\>= | a >= b | а больше или равно b
< | a < b | а меньше b
<= | a <= b | а меньше или равно b
== | a == b | а равно b
!= | a != b | а не равно b
&& | a && b | а и b истинны, b оценивается условно (если а ложно, b не вычисляется)
&#124; &#124; | a &#124; &#124; b | а или b истинно, b оценивается условно (если а истинно, b не вычисляется)
! | !a | а ложно
& | a & b | а и b истинны, b оценивается в любом случае
&#124; | a &#124; b | а или b истинно, b оценивается в любом случае
^ | a ^ b | а и b различны

### Управляющие последовательности

Оператор|Описание
:---:|---
\t | Символ табуляции.
\b | Символ возврата в тексте на один шаг назад или удаление одного символа в строке (backspace).
\n | Символ перехода на новую строку.
\r | Символ возврата каретки.
\f | Прогон страницы.
\\' | Символ одинарной кавычки.
\\" | Символ двойной кавычки.
\\ | Символ обратной косой черты (\\).

### Управляющие конструкции

#### Условный / тернарный оператор

`<логическое выражение> ? <выражение1> : <выражение2>`

```java
int a = 0;
System.out.println(a == 1 ? "One" : "Not one"); // Not one
```

### Объектно-ориентированное программирование

* Объектно-ориентированное программирование — парадигма программирования, в которой программа строится из взаимодействующих объектов.

Объекты и классы:

* Класс - шаблонная конструкция позволяющая описать объект, его свойства (переменные или поля класса) и поведение (методы класса).
* Объект - экземпляр класса который имеет состояние и поведение. Например, у собаки есть состояние - цвет, имя, порода, а также поведение — виляет хвостом, лает, ест.
* Локальные переменные - переменные, определенные внутри методов, конструкторов или блоков. Переменная объявляется и инициализируется внутри метода и будет уничтожена, когда метод завершится.
* Переменные экземпляра - переменные внутри класса, но за пределами метода. Инициализируются при создании экземпляра класса. Доступ к переменным экземпляра можно получить из любого метода, конструктора или блока.
* Переменные класса (статические переменные) - объявляются внутри класса с ключевым словом static, вне любого метода, конструктора или блока.

Создание объекта:

* Объявление - запись переменной с именем переменной и типом объекта.
* Создание экземпляра - создание объекта с помощью ключевого слова `new`
* Инициализация - за ключевым словом `new` следует вызов конструктора который инициализирует новый объект.

#### Модификаторы доступа

`public`

Публичный, общедоступный класс или член класса. Поля и методы, объявленные с модификатором public, видны другим классам из текущего пакета и из внешних пакетов.

`protected`

Такой класс или член класса доступен из любого места в текущем классе или пакете или в производных классах, даже если они находятся в других пакетах.

`default (package-private)`

Отсутствие модификатора у поля или метода класса предполагает применение к нему модификатора по умолчанию. Такие поля или методы видны всем классам в текущем пакете.

`private`

Закрытый класс или член класса, противоположность модификатору public. Закрытый класс или член класса доступен только из кода в том же классе.

Modifier|Class|Package|Subclass|World
---|:---:|:---:|:---:|:---:
public | + | + | + |+
protected | + | + | + | -
default | + | + | - | -
private | + | - | - | -

### Исключения

![exceptions1](/img/exceptions1.png)

![exceptions2](/img/exceptions2.png)

### Коллекции

![collections](/img/collections.png)

### Приемы и хитрости

#### Замер скорости компиляции

```java
long nTime = System.nanoTime(); // Start
// Код
System.out.printf("Time -> %,1.3f ms\n", (System.nanoTime() - nTime)/1_000_000.0); // Stop
// System.out.println("Fast version: " + (double) fastVersion / 1000000000 + " s");
```
### Примеры

Fibonacci

```java
public class Fibonacci {
  public static long getFibonacciNumber(int n) {
    if (n <= 0) {
      return 0;
    }
    long prev = 0;
    long curr = 1;
    for (int i = 1; i < n; ++i) {
      long next = prev + curr;
      prev = curr;
      curr = next;
    }
    return curr;
  }

  public static void printFibonacci(int max) {
    for (int i = 0; i <= max; ++i) {
      System.out.printf("fib (%d) = %d\n", i, getFibonacciNumber(i));
    }
  }

  public static void main(String[] args) {
    printFibonacci(15);
  }
}
```

FibonacciBigInteger

```java
import java.math.BigInteger;

public class FibonacciBigInteger {
  public static BigInteger getFibonacciNumber(int n) {
    if (n <= 0) {
      return BigInteger.ZERO;
    }
    BigInteger prev = BigInteger.ZERO;
    BigInteger curr = BigInteger.ONE;
    for (int i = 1; i < n; ++i) {
      BigInteger next = prev.add(curr);
      prev = curr;
      curr = next;
    }
    return curr;
  }

  public static void printFibonacciBigInteger(int max) {
    for (int i = 0; i <= max; ++i) {
      System.out.printf("fib (%d) = %d\n", i, getFibonacciNumber(i));
    }
  }

  public static void main(String[] args) {
    printFibonacciBigInteger(15);
  }
}
```

Anagrams

```java
import java.util.Arrays;

public class Anagrams {
  public static boolean areAnagrams(String a, String b) {
    char[] charsFromA = getSortedChars(a);
    char[] charsFromB = getSortedChars(b);
    return Arrays.equals(charsFromA, charsFromB);
  }

  private static char[] getSortedChars(String s) {
    char[] chars = s.toCharArray();
    Arrays.sort(chars);
    return chars;
  }

  public static void printAnagrams(String a, String b) {
    System.out.println(areAnagrams(a, b) ? "anagrams" : "not anagrams");
  }

  public static void main(String[] args) {
    printAnagrams("silent", "listen");
  }
}
```

Palindromes

```java
public class Palindromes {
  public static boolean isPalindrome(String s) {
    String normalizedText = normalize(s);
    return normalizedText.equals(reverse(normalizedText));
  }

  private static String normalize(String s) {
    return s.toLowerCase().replaceAll("\\W+", "");
  }

  private static String reverse(String s) {
    return new StringBuilder(s).reverse().toString();
  }

  public static void printPalindromes(String s) {
    System.out.println(isPalindrome(s) ? "palindrome" : "not palindrome");
  }

  public static void main(String[] args) {
    printPalindromes("Madam, I’m Adam");
  }
}
```

Polygons

```java
public class Polygons {
  public static double getArea(double[][] polygon) {
    int size = polygon.length;
    double sum = 0;
    for (int i = 0; i < size; ++i) {
      int j = (i + 1) % size;
      sum += det(polygon[i][0], polygon[i][1], polygon[j][0], polygon[j][1]);
    }
    return Math.abs(sum / 2);
  }

  private static double det(double x1, double y1, double x2, double y2) {
    return x1 * y2 - x2 * y1;
  }

  public static void main(String[] args) {
    double[][] polygon = new double[][]{{1, 1}, {1, 2}, {2, 2}, {2, 1}};
    System.out.printf("Polygon area = %1.3f\n", getArea(polygon));
  }
}
```