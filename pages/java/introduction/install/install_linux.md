##### [readme](/README.md) → [java](../../java.md) → [install](install.md) 

## Установка и настройка JDK (Linux)

### **Oracle JDK**

1. Обновить список пакетов:
    ```bash
    sudo apt update
    ```

2. Удалить старые версии Java (если необходимо):
    ```bash
    sudo apt remove --purge openjdk-* oracle-java*
    sudo apt autoremove
    ```

3. Добавить репозиторий для Oracle JDK:
    - Добавить PPA-репозиторий:
        ```bash
        sudo add-apt-repository ppa:linuxuprising/java
        ```
    - Если команда `add-apt-repository` недоступна:
        ```bash
        sudo apt install software-properties-common
        sudo apt update
        ```

4. Установить Oracle JDK (например, версию 17):
    ```bash
    sudo apt install oracle-java17-installer
    ```

5. Проверить установленную версию Java:
    ```bash
    java -version
    ```

6. Выбрать версию Java по умолчанию (если необходимо):
    ```bash
    sudo update-alternatives --config java
    ```

7. Установить переменные окружения `JAVA_HOME` (если необходимо):
    - Открыть файл `.bashrc`:
        ```bash
        nano ~/.bashrc
        ```
    - Добавить строки:
        ```bash
        export JAVA_HOME=/usr/lib/jvm/java-17-oracle
        export PATH=$PATH:$JAVA_HOME/bin
        ```
    - Обновить настройки:
        ```bash
        source ~/.bashrc
        ```

8. Проверить переменные окружения:
    ```bash
    echo $JAVA_HOME
    ```

### **OpenJDK**

1. Обновить список пакетов:
    ```bash
    sudo apt update
    ```

2. Установить OpenJDK (например, версию 17):
    ```bash
    sudo apt install openjdk-17-jdk
    ```

3. Проверить установленную версию Java:
    ```bash
    java -version
    ```

4. Выбрать версию Java по умолчанию (если необходимо):
    ```bash
    sudo update-alternatives --config java
    ```

5. Установить переменные окружения `JAVA_HOME` (если необходимо):
    - Найти путь установки OpenJDK:
        ```bash
        update-alternatives --display java
        ```
    - Открыть файл `.bashrc`:
        ```bash
        nano ~/.bashrc
        ```
    - Добавить строки:
        ```bash
        export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
        export PATH=$PATH:$JAVA_HOME/bin
        ```
    - Обновить настройки:
        ```bash
        source ~/.bashrc
        ```

6. Проверить переменные окружения:
    ```bash
    echo $JAVA_HOME
    ```

### **Установка JDK вручную**

1. Скачать JDK с официального сайта:
    - [Oracle JDK](https://www.oracle.com/java/technologies/downloads/)
    - [OpenJDK](https://jdk.java.net/)

2. Распаковать архив в `/usr/lib/jvm`:
    ```bash
    sudo mkdir -p /usr/lib/jvm
    sudo tar -xvf jdk-17*.tar.gz -C /usr/lib/jvm
    ```

3. Настроить переменные окружения:
    - Добавьте `JAVA_HOME` и `PATH` в `.bashrc`:
        ```bash
        export JAVA_HOME=/usr/lib/jvm/jdk-17
        export PATH=$PATH:$JAVA_HOME/bin
        ```

4. Обновить настройки:
    ```bash
    source ~/.bashrc
    ```

### **Автоматизация установки JDK**

1. Создать скрипт для установки:
    - Сохранить код в файл `install_java.sh`:
	    ```bash
	    #!/bin/bash
	    sudo apt update
	    sudo apt remove --purge openjdk-* oracle-java* -y
	    sudo apt autoremove -y
		
	    echo "Choose Java version to install:"
	    echo "1. Oracle JDK"
	    echo "2. OpenJDK"
	    read -p "Enter choice [1 or 2]: " choice
		
	    if [ "$choice" == "1" ]; then
	        sudo add-apt-repository -y ppa:linuxuprising/java
	        sudo apt update
	        sudo apt install -y oracle-java17-installer
	        export JAVA_HOME=/usr/lib/jvm/java-17-oracle
	    elif [ "$choice" == "2" ]; then
	        sudo apt install -y openjdk-17-jdk
	        export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-amd64
	    else
	        echo "Invalid choice. Exiting."
	        exit 1
	    fi
		
	    echo "export JAVA_HOME=$JAVA_HOME" >> ~/.bashrc
	    echo "export PATH=\$PATH:\$JAVA_HOME/bin" >> ~/.bashrc
	    source ~/.bashrc
	    java -version
	    ```

2. Сделать скрипт исполняемым:
    ```bash
    chmod +x install_java.sh
    ```

3. Запустить скрипт:
    ```bash
    ./install_java.sh
    ```
