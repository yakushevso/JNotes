##### [readme](/README.md) → [java](../java.md)

### Рецепты

#### Замер скорости компиляции

```java
// Измерение времени в наносекундах
long startTime = System.nanoTime();
java.util.Arrays.sort(new int[100000000]); // Пример замеряемой операции
System.out.printf("Time: %.6f seconds\n", (double) (System.nanoTime() - startTime) / 1_000_000_000);
```

#### Очистка консоли

```java
void clearConsole() {
	try {
		// Выбор операционной системы (Windows / Linux)
        var clear = System.getProperty("os.name").contains("Windows") 
	        ? new ProcessBuilder("cmd", "/c", "cls") 
	        : new ProcessBuilder("clear");
        clear.inheritIO().start().waitFor();
    } catch (InterruptedException | IOException e) {
	    System.err.println("Error clearing console: " + e.getMessage());
    }
}
```