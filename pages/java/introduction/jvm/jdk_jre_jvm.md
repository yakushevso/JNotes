##### [readme](/README.md) → [java](../../java.md) → [jvm_basics](jvm_basics.md)

## Основные термины: JDK, JRE и JVM

![jvm_jre_jdk](https://i.imgur.com/4ps8Jsq.jpeg)

### **JDK (Java Development Kit)** 

Пакет для разработки программ.

Включает в себя:

- **JRE** (Java Runtime Environment)
- Загрузчик кода Java
- Компилятор `javac`
- Архиватор `jar`
- Генератор документации `javadoc`
- Другие утилиты для разработки (`jdb`, инструмент для отладки, ...)

### **JRE (Java Runtime Environment)**

Окружение, необходимое для запуска Java-программ. 

Включает в себя:

- **JVM** (Java Virtual Machine)
- Стандартную библиотеку (пакеты `lang`, `util`, пакеты для работы с различными форматами, базами данных, пользовательским интерфейсом, ...)

### **JVM (Java Virtual Machine)**

Виртуальная машина отвечает за выполнение байт-кода Java (.class).

Включает в себя:

- **Подсистема загрузчика классов (Class Loader)** — загружает байт-код и проверяет его безопасность
- **Области данных времени выполнения (Runtime Data Areas)** — различные области памяти, такие как стек, куча, область методов и т.д.
- **Двигатель исполнения (Execution Engine)** — интерпретирует или компилирует байт-код в машинный код
- **Сборщик мусора (Garbage Collector)** — управляет памятью и удаляет неиспользуемые объекты

#### **HotSpot JVM**

**HotSpot** — одна из основных виртуальных машин JVM, используемая в большинстве дистрибутивов Java, включая Oracle JDK и OpenJDK. Включает в себя множество оптимизаций, таких как:

- **Just-In-Time (JIT)** компиляция, ускоряющая выполнение байт-кода.
- Поддержку различных сборщиков мусора, таких как **G1**, **CMS**, **Parallel GC**, и **ZGC**.
- Высокую производительность для многопоточных приложений.

> До Java 11 для запуска программы достаточно было JRE. Однако с выходом Java 11 JRE больше не поставляется отдельно, и для работы с JVM 11 и новее нужно устанавливать JDK.