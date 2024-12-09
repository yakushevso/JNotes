##### [readme](/README.md) → [java](pages/java/java.md) → [jvm_basics](pages/java/introduction/jvm/jvm_basics)

## Основные термины: JDK, JRE и JVM

![jvm_jre_jdk](https://i.imgur.com/4ps8Jsq.jpeg)

- **JDK (Java Development Kit)** — пакет для разработки программ.
	- Включает в себя JRE, загрузчик кода java, компилятор javac, архиватор jar, генератор документации javadoc и другие утилиты.
- **JRE (Java Runtime Environment)** — окружение, необходимое для запуска Java-программ. 
	- Включает в себя JVM, стандартную библиотеку (пакеты lang, util, пакеты для работы с различными форматами, базами данных, пользовательским интерфейсом и другие пакеты).
- **JVM (Java Virtual Machine)** — виртуальная машина отвечает за выполнение байт-кода Java (.class).

> До Java 11 для запуска программы достаточно было JRE. Однако с выходом Java 11 JRE больше не поставляется отдельно, и для работы с JVM 11 и новее нужно устанавливать JDK.