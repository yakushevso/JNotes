##### [<-- back to OOP](../../java/oop/oop.md)

## Конструктор класса

* Конструктор - специальный метод, который вызывается при создании нового объекта.
* Конструкторы выполняют инициализацию объекта.
* Имя конструктора совпадает с именем класса, включая регистр.
* В отличие от метода, конструктор никогда ничего не возвращает.
* Конструкторы поддерживают перегрузку.
* Если в классе не определено ни одного конструктора, то для этого класса автоматически создается конструктор без параметров.

```java
public class Program {
    public static void main(String[] args) {
        Person bob = new Person(); // вызов первого конструктора без параметров
        bob.displayInfo(); // Name: Undefined - Age: 18

        Person tom = new Person("Tom"); // вызов второго конструктора с одним параметром
        tom.displayInfo(); // Name: Tom - Age: 19

        Person sam = new Person("Sam", 25); // вызов третьего конструктора с двумя параметрами
        sam.displayInfo(); // Name: Sam - Age: 25
    }
}

class Person {
    String name;
    int age;
    
    Person() {
        name = "Undefined";
        age = 18;
    }
    
    Person(String n) {
        name = n;
        age = 19;
    }
    
    Person(String n, int a) {
        name = n;
        age = a;
    }
    
    void displayInfo() {
        System.out.printf("Name: %s - Age: %d\n", name, age);
    }
}
```