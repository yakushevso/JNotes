##### [readme](/README.md) → [java](../../java.md) → [jvm_basics](jvm_basics.md)

## Сборка, исполнение и архивация

![jvm_program_cycle](https://i.imgur.com/64ikaTm.jpeg)

### Компиляция и исполнение кода

#### **Пример структуры каталогов**

```bash
/project
├── bin/  # Скомпилированные классы
│	└── com/
│		└── example/
│			├── Main.class
│			└── utils/
│				└── Helper.class
├── lib/  # Библиотеки и внешние зависимости
│	└── (jar файлы)
└── src/  # Исходный код
	└── com/
		└── example/
            ├── Main.java  # Точка входа в приложение
            └── utils/
                └── Helper.java
    
```

#### **Компиляция**

Команда `javac` используется для преобразования исходного код Java (`.java` файлы) в байт-код (`.class` файлы).

```bash
javac [ключи] [исходники]
```

- `[ключи]` — дополнительные параметры или флаги, которые изменяют процесс компиляции, например: `-d <папка>`, `-source <версия>`, `-target <версия>`.
- `[исходники]` — имена файлов исходного кода Java, например: `Main.java`, `Example.java`.

```bash
javac -d bin -cp lib/* -sourcepath src src/com/example/Main.java
```

- `-d bin` — сохраняет скомпилированные `.class` файлы в папку `bin`, соблюдая структуру пакетов.
- `-cp lib/*` — (сокращение от `-classpath`) подключает внешние библиотеки или зависимости из папки `lib`, для использования сторонних `.jar` файлов.
- `-sourcepath src` — указывает папку в которой компилятору необходимо искать иерархию исходных файлов.
- `src/com/example/Main.java` — компилирует указанный файл вместе с его зависимостями.

#### **Запуск кода**

Команда `java` используется для выполнения скомпилированного байт-кода Java (`.class` файлы) с помощью JVM.

```markup
java [ключи] класс [аргументы]
```

- `[ключи]` — дополнительные параметры или флаги для управления процессом выполнения программы, например: `-Xmx<размер>`, `-jar`.
- `класс` — название класса, содержащего `public static void main(String[] args)` метод, который является точкой входа для программы.
- `[аргументы]` — опциональные параметры для передачи в метод `main`.

```bash
java -cp bin com.example.Main
```

`-cp bin` — указывает на папку, где находятся скомпилированные классы.
`com.example.Main` — имя запускаемого класса с учетом иерархии пакетов.

### **Архивация файлов (JAR - Java Archive)**

#### Структура JAR-файла

```bash
myApp.jar
├── META-INF/
│   └── MANIFEST.MF  # Манифестный файл JAR-архива
├── com/
│   └── example/
│       └── Main.class  # Основной скомпилированный класс
├── resources/
│   └── config.properties  # Ресурсы приложения
└── lib/
    └── dependency.jar  # Внешние зависимости или библиотеки
```

- **`META-INF/`** – обязательный каталог с манифестом (`MANIFEST.MF`).
- **`.class файлы`** – скомпилированные классы Java.
- **`resources`** – дополнительные файлы (изображения, текстовые файлы и др.).
- **`MANIFEST.MF`** — содержит метаинформацию, такую как версия, главный класс для запуска (Main-Class) и зависимости.
	```bash
	Manifest-Version: 1.0
	Main-Class: com.example.Main
	Implementation-Version: 1.0.0
	Class-Path: lib/dependency.jar
	Created-By: Maven 3.8.1
	
	```
	- Для обозначения имени пакета используется **точка** вместо **косой черты** (например, `com.example`).
	- Последняя строка манифеста должна заканчиваться новой строкой или символом каретки, в противном случае она не будет корректно обработана.

#### **Создание JAR-архива**

```bash
jar -cf jar-файл входной-файл(ы)
```

- Команда для создания JAR-архива с классами и ресурсами.
	- **`-c`** — флаг, который указывает на создание нового архива.
	- **`-f`** — флаг для указания, что вывод должен быть направлен в файл.
	- **`jar-файл`** — имя выходного JAR-архива с расширением `.jar`.
	- **`входной-файл(ы)`** — список файлов, которые нужно включить в JAR-архив. Это могут быть `.class` файлы или другие ресурсы.

	```bash
	jar -cf myApp.jar *.class
	```
- Команда автоматически создаст файл `MANIFEST.MF` и поместит его в каталог `META-INF`.

#### **Запуск JAR-архива**

- Если `Main-Class` отсутствует или нужно указать основной класс вручную:

	```bash
	java -cp myApp.jar com.example.Main
	```

- Если `Main-Class` присутствует в `MANIFEST.MF`:
	```bash
	java -jar myApp.jar
	```

#### **Кроме JAR, также существуют другие архивы, связанные с Java**

- WAR (**W**eb **A**pplication A**r**chive) - содержит в себе приложение для веба.
- EAR (**E**nterprise **A**pplication A**r**chive) - содержит в себе энтерпрайз приложение (обычно из нескольких модулей).
- APK (**A**ndroid A**p**plication Pac**k**age) - содержит в себе приложение для Android.