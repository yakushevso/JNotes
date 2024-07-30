##### [readme](/README.md) → [java](../../java.md) → [jvm_basics](jvm_basics.md)

## Параметры JVM

### **Опции JVM**

- Опции позволяют настраивать различные аспекты JVM при запуске программы.
- Формат: `java [options] classname [args]` или `java [options] -jar filename [args]`.

### **Стандартные опции JVM**

- Влияют на выполнение приложения, включая вывод логов и управление окружением.
- Стандартные опции начинаются с `-`.
	- **`-verbose:gc`** — выводит информацию о сборке мусора.
		```bash
		java -verbose:gc Main
		```
	- **`-verbose:class`** — выводит информацию о загруженных классах.
		```bash
		java -verbose:class Main
		```

### **Свойства системы**

- **`D`** означает "define" и указывает, что данная опция является пользовательской.
- **`-D<property_name>=<property_value>`**  — устанавливает значение системного свойства.
	```bash
	java -Dfile.encoding=UTF-8 Main
	```
- **`-Dmode=Manual`**  — создание собственного варианта.
-  Можем получать их через `System.getProperty("property_name или manual");`

### **Нестандартные опции (начинаются с -X)**

- Могут изменять режим компиляции, размеры памяти и другие параметры.
- Принимают параметры размера в байтах, но можно указывать в `k`/`K` килобайтах, `m`/`M` мегабайтах, и `g`/`G` гигабайтах.
- **`-Xss<size>`** — задает размер стека для потоков.
	```bash
	java -Xss4096k Main
	```
- **`-Xcomp`** — компилирует все методы при первом вызове.
	```bash
	java -Xcomp Main
	```

### **Расширенные параметры (начинаются с -XX)**

- Управляют производительностью и поведением JVM.
- Можно поставить `+`или , `-`чтобы включить или отключить опцию.
- **`-XX:+PrintCommandLineFlags`** — печатает выбранные параметры JVM.
	```bash
	java -XX:+PrintCommandLineFlags Main
	```
- **`-XX:+PrintCompilation`** — выводит каждый скомпилированный метод.
	```bash
	java -XX:+PrintCompilation Main
	```
- **`-XX:+UseSerialGC`** — включает последовательный сборщик мусора.
	```bash
	java -XX:+UseSerialGC Main
	```

### **Параметры для JIT-компилятора**

- Управляют компиляцией Just-In-Time (JIT).
- **`-XX:+PrintInlining`** — выводит информацию о встраивании методов.
	```bash
	java -XX:+PrintInlining Main
	```
- **`-XX:+PrintInlining`** — включает вывод решений JIT-компилятора о встраивании методов.
	```bash
	java -XX:+UnlockDiagnosticVMOptions -XX:+PrintInlining Main
	```

### **Параметры для логирования и отладки**

- Для сбора информации о работе JVM.
- **`-XX:LogFile=path`** — указывает файл для записи логов.
	```bash
	java -XX:LogFile=C:/JVM/logfile.log Main
	```

### **Параметры для сборщика мусора**

- Настройка поведения сборщика мусора для оптимизации памяти.
- **`-XX:+UseSerialGC`** — позволяет использовать последовательный сборщик мусора.
	```bash
	java -XX:+UseSerialGC Main
	```
- **`-XX:+UseStringDeduplication`** — активирует дедупликацию строк.
	```bash
	java -XX:+UseStringDeduplication Main
	```