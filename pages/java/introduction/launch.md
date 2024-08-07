##### [<-- back to Java](../java.md)

## Сборка, исполнение и архивация

Компиляция кода:

`javac HelloWorld.java`

* На выходе получаем файл HelloWorld.class

Запуск HelloWorld.class:

`java -cp . HelloWorld`
* Ключ `-cp` сокращение от `-classpath` указывает компилятору, где искать исходные файлы.

Компиляция кода с созданием каталогов:

`javac -d bin src/HelloWorld.java`

На выходе получаем каталоги:
* Исходный файл - `src/HelloWorld.java`
* Скомпилированный файл - `bin/HelloWorld.class`

Запуск bin/HelloWorld.class из каталога:

`java -cp ./bin HelloWorld`

Архивация файлов (JAR - Java Archive):

`jar -cf jar-файл входной-файл(ы)`
* Ключ `c` показывает, что необходимо создать (create) JAR-файл.
* Ключ `f` показывает, что необходимо направить вывод в файл, а не в стандартный поток вывода.
* `jar-файл` - название выходного JAR-файла с расширением `.jar`
* `входной-файл(ы)` - список файлов через пробел, которые необходимо поместить в JAR-файл.
* Команда `jar` автоматически создает файл `MANIFEST.MF` и помещает в каталог `META-INF`

Кроме JAR, также существуют другие архивы, связанные с Java:

* WAR (**W**eb **A**pplication A**r**chive) - содержит в себе приложение для веба.
* EAR (**E**nterprise **A**pplication A**r**chive) - содержит в себе энтерпрайз приложение (обычно из нескольких модулей).
* APK (**A**ndroid A**p**plication Pac**k**age) - содержит в себе приложение для Android.