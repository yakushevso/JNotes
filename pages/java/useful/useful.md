##### [<-- back to Java](../../java/java.md)

### Полезное

#### Замер скорости компиляции

```java
long nTime = System.nanoTime(); // Start
// Код
System.out.printf("Time -> %,1.3f ms\n", (System.nanoTime() - nTime)/1_000_000.0); // Stop
// System.out.println("Fast version: " + (double) fastVersion / 1000000000 + " s");
```