##### [<-- back to OOP](../../java/oop/oop.md)

## Типы переменных

Локальные переменные:

* Переменные, определенные внутри методов, конструкторов или блоков.
* Переменная объявляется и инициализируется внутри метода и будет уничтожена, когда метод завершится.
* Модификаторы доступа нельзя использовать для локальных переменных.
* Локальные переменные видны только внутри объявленного метода, конструктора или блока.
* Локальные переменные реализованы на уровне стека.
* Локальные переменные не имеют значение по умолчанию, значение должно быть присвоено до использования.

```java
public class Test {
    public static void main(String[] args) {
        int first = 0;
        fisrt = fisrt + 7; // 7
        int second;
        // second = second + 7 // Error: variable number might not have been initialized
    }
}   
```

Переменные экземпляра:

* Переменные определяются внутри класса, но за пределами метода, конструктора или любого блока.
* Когда для объекта в куче выделяется место, создается слот для каждого значения переменной экземпляра.
* Переменные экземпляра создаются при создании объекта с использованием ключевого слова `new` и уничтожаются при уничтожении объекта.
* Модификаторы доступа могут быть заданы для переменных экземпляра.
* Доступ к переменным экземпляра можно получить из любого метода, конструктора или блока.
* Переменные экземпляра имеют значения по умолчанию. Для чисел значение по умолчанию равно 0, для логических значений — false, а для ссылок на объекты — null.
* Значения могут быть присвоены во время объявления или в конструкторе.
* Переменная экземпляра может быть вызвана напрямую через имя переменной внутри класса. В статичных методах их следует вызывать с использованием полного имени `ObjectName.varName`

```java
public class Test {
    public int first; // Переменная экземпляра открыта для любого дочернего класса
    private int second; // Переменная экземпляра видна только в Test

    // Значение переменной first присваивается в конструкторе
    public Test(int num) {
        first = num;
    }
        
    // Значение переменной second присваивается в методе
    public void method (int num) {
        second = num;
    }

    public static void main(String[] args) {
        Test test = new Test(7);
        test.method(5);
    }
}   
```

Переменные класса (статические переменные):
* Объявляются внутри класса с ключевым словом static, вне любого метода, конструктора или блока.
* Статическая переменная, видна из всех экземпляров этого объекта, и ее значение не меняется от экземпляра к экземпляру, существует независимо от каких-либо экземпляров, поэтому оно принадлежит всему классу.
* Создается только одна копия каждой статической переменной в классе, независимо от того, сколько объектов создано из него.
* Статические переменные используются редко, кроме когда объявляются как константы. Константы - переменные, которые объявлены как public/private, final и static. Константы никогда не меняются от первоначального значения.
* Статические переменные создаются при запуске программы и уничтожаются при остановке программы.
* Статические переменные хранятся в "статической памяти" специальном пуле в памяти JVM, называемом Metaspace.
* Видимость похожа на переменные экземпляра. Однако большинство статических переменных объявляются общедоступными, поскольку они должны быть доступны для пользователей класса.
* Значения по умолчанию такое же, как и у переменных экземпляра. Для чисел по умолчанию равно 0, для данных типа boolean – false; и для ссылок на объект – null. Значения могут быть присвоены при объявлении или в конструкторе. Кроме того, они могут быть присвоены в специальных блоках статического инициализатора.
* Доступ к статическим переменным можно получить, вызвав имя класса `ClassName.varName`
* При объявлении переменных класса как `public static final` имена переменных (константы) пишутся в верхнем регистре.
* Если доступ к переменным осуществляется из внешнего класса, к константе следует обращаться как к `ClassName.CONSTANTA`

```java
public class Test {
    public static int first;
    static int second;
    public static final int TEST = 5; // Объявление статичной переменной (константа)

    public static void main(String[] args) {
        first = 7;
        Test.second = TEST; // 5
    }
}
```