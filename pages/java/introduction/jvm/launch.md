##### [readme](/README.md) → [java](../../java.md) → [jvm_basics](jvm_basics.md)

## Сборка, исполнение и архивация

![jvm_program_cycle](https://i.imgur.com/64ikaTm.jpeg)

### **Компиляция кода**

```bash
javac HelloWorld.java
```

- Компиляция исходного файла `HelloWorld.java` в байт-код Java, результатом которой является файл `HelloWorld.class`.

### **Запуск HelloWorld.class**

```bash
java -cp . HelloWorld
```

- Запуск скомпилированного класса `HelloWorld`. Ключ `-cp` (сокращение от `-classpath`) указывает Java виртуальной машине (JVM), где искать скомпилированные классы. В данном случае это текущая директория `.`.

### **Компиляция кода с созданием каталогов**

```bash
javac -d bin src/HelloWorld.java
```

- Компиляция исходного файла `src/HelloWorld.java` с созданием каталогов для скомпилированных файлов.
    - **`-d bin`** — флаг `-d` указывает директорию для скомпилированных классов. В данном случае это директория `bin`. Если папка не существует, она будет автоматически создана. Скомпилированный файл `HelloWorld.class` будет помещен в эту папку.
    - **`src/HelloWorld.java`** — исходный файл, который компилируется в байт-код.

### **Запуск скомпилированного класса из каталога**

```bash
java -cp ./bin HelloWorld
```

- Запуск скомпилированного класса `HelloWorld`, который был сохранен в папке `bin`. Параметр `-cp ./bin` указывает Java, что классы находятся в каталоге `bin`, и они будут использованы для запуска.

### **Компиляция нескольких файлов**

```bash
javac -d bin ./src/*
```

- Компиляция нескольких исходных файлов. Ключ `-d` указывает директорию, куда будут помещены скомпилированные классы. В данном случае это директория `bin`.
    - **`bin`** — каталог для скомпилированных файлов.
    - **`./src/*`** — указывает на все исходные файлы в каталоге `src`.

### **Рекурсивная компиляция**

```bash
javac -d bin -sourcepath src src/**/*.java
```

- Рекурсивная компиляция всех `.java` файлов из каталога `src` и его подкаталогов. Команда сохраняет структуру пакетов при компиляции.
    - **`-d`** — флаг для указания директории для скомпилированных классов.
    - **`-sourcepath`** — флаг, который указывает начальный путь к исходным файлам (в данном случае это каталог `src`).
    - **`src/**/*.java`** — шаблон, который рекурсивно выбирает все `.java` файлы в каталоге `src` и его подкаталогах:
        - `src/` — корневой каталог для исходных файлов.
        - `**/` — специальный глоб, который выбирает все подкаталоги на любом уровне.
        - `*.java` — выбор всех `.java` файлов.
    - Скомпилированные классы сохраняются в `bin`, при этом структура пакетов сохраняется.

### **Запуск скомпилированного класса**

#### Пример структуры каталогов

```
bin/
└── dir1/
	└── dir2/
	└── Main.class
```

#### Запуск

```bash
java -classpath ./bin dir1.dir2.Main
```

- Запуск скомпилированного класса `Main`, который находится в пакете `dir1.dir2`. Ключ `-classpath` указывает директорию скомпилированных классов, в данном случае это `bin`.
    - **`./bin`** — директория, где находятся скомпилированные классы.
    - **`dir1.dir2.Main`** — полный путь к классу, включая имя пакета (без расширения `.class`).

#### Альтернативный запуск с использованием текущей директории

```bash
java -cp . dir1.dir2.Main
```

- Альтернативная запись с использованием флага `-cp` (аналог `-classpath`), который указывает на текущую директорию как путь для поиска классов.
    - **`.`** — текущая директория, где находятся скомпилированные классы.

### **Архивация файлов (JAR - Java Archive)**

```bash
jar -cf jar-файл входной-файл(ы)
```

- Команда для создания JAR-архива с классами и ресурсами.
    - **`-c`** — флаг, который указывает на создание нового архива.
    - **`-f`** — флаг для указания, что вывод должен быть направлен в файл.
    - **`jar-файл`** — имя выходного JAR-архива с расширением `.jar`.
    - **`входной-файл(ы)`** — список файлов, которые нужно включить в JAR-архив. Это могут быть `.class` файлы или другие ресурсы.
- Команда автоматически создаст файл `MANIFEST.MF` и поместит его в каталог `META-INF`.

> ### Кроме JAR, также существуют другие архивы, связанные с Java:
> 
> - WAR (**W**eb **A**pplication A**r**chive) - содержит в себе приложение для веба.
> - EAR (**E**nterprise **A**pplication A**r**chive) - содержит в себе энтерпрайз приложение (обычно из нескольких модулей).
> - APK (**A**ndroid A**p**plication Pac**k**age) - содержит в себе приложение для Android.