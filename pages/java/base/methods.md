##### [<-- back to Java](../../java/java.md)

### Методы

* Метод - блок кода, состоящий из ряда инструкций, являющийся в основном поведением. Содержит возвращаемый тип, название, аргументы и тело метода.

```java
public static int methodName(int a, int b) {
    // тело метода
    return возвращаемое_значение;
}
```

* `public static` (модификатор) - Определяет тип доступа к методу (его необязательно использовать)
* `int` (тип возвращаемого значения) - Метод может возвращать (int) или не возвращать (void) значение.
* `methodName` - имя метода.
* `int a, int b` (параметры метода) - Метод на входе может принимать аргументы в любого типа в любом порядке и количестве (метод может не иметь ни одного аргументов)
* `return` - (оператор возврата значения) - После оператора return указывается возвращаемое значение, которое является результатом метода.

Типы методов:

```java
// Без возвращаемого значения с аргументами
public void methodName(int a, int b) {
    System.out.println(a + b); // Выводит в консоль сумму a и b
}

// Без возвращаемого значения и без аргументов
public void methodName() {
    System.out.println("Текст") // Выводит в консоль текст
}

// С возвращаемым значением и аргументами
public int methodName(int a, int b) {
    return a + b; // возвращает сумму a и b
}

// С возвращаемым значением и без аргументов
public int methodName() {
    int a = 5, b = 7;
    return a + b; // возвращает сумму a и b
}
```

Вызов метода:

```java
public class Test {

    public static void methodName() {
        System.out.println("Текст");
    }

    public static void methodVoid(int a, int b) {
        System.out.println(a + b);
    }

    public static int methodReturn(int a, int b) {
        return a + b;
    }

    public static void main(String[] args) {
        methodName();
        methodVoid(5, 7);
        System.out.println(methodReturn(4, 5));
    }
}
```

Перегруженные методы:

* Если класс имеет два или более метода с одинаковыми именами, но разными параметрами.
* Перегруженные методы могут возвращать значение разного типа при условии, что параметры методов будут отличаться.

```java
public class Test {

    public static void sum(int a, int b) {
        System.out.println(a + b);
    }

    public static void sum(int a, int b, int c) {
        System.out.println(a + b + c);
    }

    public static int sum(int a, int b, int c, int d) {
        return a + b + c + d;
    }

    public static void main(String[] args) {
        sum(4, 5);
        sum(4, 5, 7);
        System.out.println(sum(1, 2, 3, 4));
    }
}
```

VarArgs (Список переменных аргументов):

* Специальный синтаксис для массива аргументов (Поддерживается с Java 5).
* Аргумент VarArgs должен стоять последним в списке аргументов, перед ним сколько угодно.

```java
int max(int... num); // max(1, 2, 3, 4);
int min(String s, int... num) // min("Numbers", 1, 2, 3, 4)
```

#### Использование аргументов командной строки

* Передача информации в программу через командную строку при запуске.
* Аргумент командной строки - это информация, которая следует непосредственно за именем программы в командной строке при ее выполнении.

```java
public class Test {
    public static void main(String[] args) {
        for(int i = 0; i < args.length; i++) {
            System.out.println("args[" + i + "]: " + args[i]);
        }
    }
}
```

Запуск программы через командную строку с параметрами:

`$java Test Текст 7 -5`

Результат:

```java
args[0]: Текст
args[1]: 7
args[2]: -5
```

#### Ключевое слово this

* Когда у переменной экземпляра класса и переменной метода/конструктора одинаковые имена.

```java
class Test { 
    int num;
    Test(int num) {
        this.num = num; // this указывает на переменную экземпляра класса
    }
}
```

* Если нужно вызвать конструктор одного типа из другого (явный вызов конструктора)

```java
class Test { 
    int num
    Test() {
       this(7); // Вызывает конструктор с одним параметром
    }
    
    Test(int num) {
       this.num = num;
    }
}
```