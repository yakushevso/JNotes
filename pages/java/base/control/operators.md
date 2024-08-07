##### [<-- back to Loops and operators](../../../java/base/control/control.md)

## Операторы принятия решений

### Оператор if

```java
if (выражение) {
    // Выполняется, если логическое выражение истинно
}
```

### Вложенный оператор if

```java
if (выражение1) {
   // Выполняется, если логическое выражение1 истинно
   if (выражение2) {
      // Выполняется, если логическое выражение2 истинно
   }
}
```

### Оператор if...else if...else

```java
if (выражение1) {
    // Выполняется, если логическое выражение1 истинно
} else if (выражение2) {
    // Выполняется, если логическое выражение2 истинно
    ...
} else if (выражениеN) {
    // Выполняется, если логическое выражениеN истинно
} else {
    //Выполняется, если все остальное ложно
}
```

### Оператор switch...case

* Переменные, которые используются в операторе switch, могут быть только целые числа, конвертированные в целые числа (byte, short, char), строки и перечисления.
* Когда переменная switch равна оператору case, операторы следующие за case будут выполняться до тех пор, пока не будет достигнут оператор break.
* Не каждый case должен содержать break. Если отсутствует break, поток управления попадет на следующие case, до тех пор пока break не будет достигнут.
* Оператор switch может иметь дополнительный default case, который должен находиться в конце switch. Default case может быть использован для выполнения задачи, когда ни один из case является правильным. Break не требуется в default case.

```java
switch (выражение) {
        case значение1:
        // Выполнимся, если выражение равно значению1
        break;
        case значение2:
        // Выполнимся, если выражение равно значению2
        break;
        ...
        case значениеN:
        // Выполнимся, если выражение равно значениюN
        break;
        default: // можно не использовать
        // Выполнится, в любом случае
}
```

### Условный / тернарный оператор

`<логическое выражение> ? <выражение1> : <выражение2>`

```java
int a = 0;
System.out.println(a == 1 ? "One" : "Not one"); // Not one
```

### Оператор instanceof

`<ссылочная переменная объекта> instanceof <тип класса/интерфейса>`

* Оператор проверяет, относится ли объект к определенному типу.
* Используется только для переменных ссылки на объект.

```java
String str = "String";
boolean res = str instanceof String; // true
Vehicle a = new Car();
boolean res =  a instanceof Car; // true
```