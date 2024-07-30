##### [<-- back to Java](../../java/java.md)

## Приведение типов

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