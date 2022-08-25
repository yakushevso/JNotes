## Git

### Установка Git
https://gitforwindows.org/ <br>
https://git-scm.com/book/ru/v2/Введение-Установка-Git

`git --version`

### Генерация ключа MSysGit для GitHub
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`<br>
`eval "$(ssh-agent -s)"`<br>
`ssh-add ~/.ssh/id_rsa`<br>
`clip < ~/.ssh/id_rsa.pub`<br>
`ssh -T git@github.com`

### Подгрузка репозитория GitHub в IDEA
`git init`<br>
`git remote add origin SSH_GIT_PROJECT`<br>
`git remote -v`<br>
`git checkout -b master`<br>
`git fetch`

### Настройки Git в IDEA
Файл **.gitignore**<br>
`*.class`<br>
`target/`<br>
`*.iml`<br>
`.idea/`

### Локальный конфиг
`C:\Users\Admin\IdeaProjects\education\.git\config`

###Глобальный конфиг
`C:\Program Files\Git\etc\gitconfig`

### Настройка Alias консоль
`git config --global alias.co checkout`<br>
`git config --global alias.br branch`<br>
`git config --global alias.ci commit`<br>
`git config --global alias.st status`<br>
`git config --global alias.ls "log --oneline --graph --decorate --all"`<br>
`git config --global alias.lsf "log --oneline --graph --decorate --all --pretty=format:'%C(auto)%h%d %C(reset)%s %C(green)(%cD)%C(reset) %C(blue)<%an>'"`<br>
`git config --global alias.rf reflog --date=iso`<br>
`git config --global alias.cim commit -m`

### Настройка Alias файл
`C:\Users\Admin\.gitconfig`

`co = checkout`<br>
`br = branch`<br>
`ci = commit`<br>
`st = status`<br>
`ls = log --oneline --graph --decorate --all`<br>
`lsf = log --oneline --graph --decorate --all --pretty=format:'%C(auto)%h%d %C(reset)%s %C(green)(%cD)%C(reset) %C(blue)<%an>'`<br>
`rf = reflog --date=iso`<br>
`cim = commit -m`

### Конфигурационные команды
`git config --global user.name "name"` // установить имя, которое будет прикрепляться к коммиту.<br>
`git config --global user.email "email address"` // установить email, который будет прикрепляться к коммиту.<br>
`git config --global color.ui auto` // включить полезную подсветку командной строки.<br>
`git config --global push.default current` // обновлять удаленную ветку с таким же именем, что и локальная, при пуше изменений (если не указано иного).<br>
`git config --global core.editor <editor>` // установить редактор для редактирования сообщений коммита.<br>
`git config --global diff.tool <tool>` // установить программу для разрешения конфликтов при слиянии.

### Нотации (~ и ^)

![notations](/img/notations.png)

HEAD\~ — это сокращенная запись HEAD\~1 и означает первого родителя коммита. HEAD\~2 означает первого родителя у первого родителя коммита. HEAD\~n можно понимать как «n коммитов перед HEAD» или «n-ый предок HEAD».

HEAD^ (или HEAD^1) тоже означает первого родителя коммита. Но вот HEAD^2 означает второго родителя коммита. Помните, коммит, представляющий собой нормальное слияние (merge), имеет двух родителей: первый родитель — это коммит, в который осуществляется слияние, а второй родитель — коммит, который был слит. Вообще говоря, слияния могут иметь произвольно много родителей (octopus merges).

Операторы ^ и \~ могут выстраиваться в линию, например, HEAD\~3^2 будет означать второго родителя предка HEAD третьего уровня; HEAD^^2 — второго родителя первого родителя HEAD; HEAD^^^ — это просто эквивалент HEAD\~3.




### Общие команды

`git init <project-name>` // создать новый локальный репозиторий с заданным именем.<br>
`git clone <url>` // загрузить проект и его полную историю изменений.<br>
`git add .` // сделать все измененные файлы готовыми для коммита.<br>
`git add <fileName>` // сделать указанный файл готовым для коммита.<br>
`git add '*.txt'` // добавить только файлы, соответствующие указанному выражению.<br>
`git add --patch fileName` // позволяет выбрать какие изменения из файла добавятся в коммит.<br>
`git mv [oldFile] [renamedFile]` // изменить имя файла и добавить в индекс коммита.<br>
`git commit` // записать изменения в репозиторий. для написания сообщения откроется назначенный редактор.<br>
`git commit -m "commit"` // записать изменения с заданным сообщением.<br>
`git commit -am "commit”` // создает коммит всех проиндексированных изменений с заданным сообщением.<br>
`git commit --amend / -m` // добавить изменения к последнему коммиту / без вызова редактора.<br>
`git push` // запушить текущую ветку в удаленную ветку.<br>
`git push <remote> <branch>` // запушить ветку в указанный репозиторий и удаленную ветку. (origin master / HEAD)<br>
`git push <remote> :<branch>` // в удаленном репозитории удалить заданную ветку.<br>
`git push -u origin master` // если удаленная ветка не установлена как отслеживаемая, то сделать ее такой.<br>
`git push -f origin HEAD` // перезаписать удаленный репозиторий локальным.<br>
`git push origin --delete <branch>` // удаление удаленной ветки.<br>
`git fetch` // загружает коммиты, файлы и ссылки из удаленного репозитория локальный репозиторий<br>
`git fetch <remote>` // загрузить всю историю с заданного удаленного репозитория.<br>
`git merge` // слияние одной или нескольких веток в текущую.<br>
`git merge <branch>` // соединить изменения в текущей ветке с изменениями из заданной.<br>
`git merge --no-ff <branch>` // соединить ветки без режима “fast forwarding”.<br>
`git merge <remote>/<branch>` // слить изменения локальной ветки и заданной удаленной.<br>
`git pull` // загрузить историю и изменения удаленной ветки и произвести слияние с текущей веткой. (fetch + merge)<br>
`git pull <remote> <branch>` // указать конкретную удаленную ветку для слияния.<br>
`git branch` // список всех локальных веток в текущей директории.<br>
`git branch <branchName>` // создать новую ветку.<br>
`git branch -a` // посмотреть полный список локальных и удаленных веток.<br>
`git branch -d <branch>` // удалить заданную ветку.<br>
`git branch -D <branch>` // принудительно удалить заданную ветку, игнорируя ошибки.<br>
`git branch -m <oldName> <newName>` // переименовать ветку.<br>
`git branch -v` // последний коммит на каждой из веток.<br>
`git branch --merged / --no-merged` // показать все ветки, слияние для которых было выполнено/не выполнено <br>
`git checkout` // переключение между ветками.<br>
`git checkout -b <branchName>` // создать новую ветку и переключиться на нее.<br>
`git checkout <branchName>` // переключиться на указанную ветку и обновить рабочую директорию.<br>
`git checkout -b <branchName> <remote>/<branch>` // создание новой ветки на основе удаленного репозитория.<br>
`git checkout <fileName>` // вернуть файл в первоначальное состояние если он еще не был добавлен в индекс коммита.<br>
`git checkout -- .` // сброс изменений в рабочей директории (красные коммиты).<br>
`git checkout <commit>` // переключение на конкретный коммит (состояние Detached HEAD).<br>
`git diff` // показать изменения в файлах, которые еще не были добавлены в индекс коммита (staged)..<br>
`git diff --staged` // показать что было добавлено в индекс с помощью git add, но еще не было закоммиченно.<br>
`git diff HEAD` // показать что изменилось с последнего коммита.<br>
`git diff HEAD^` // показать что изменилось с предпоследнего коммита.<br>
`git diff <branch>` // сравнить текущую ветку с заданной.<br>
`git diff <fileBranch>..<secondBranch>` // посмотреть различия между двумя заданными ветками.<br>
`git diff --stat` // показать статистику какие файлы были изменены и как.<br>
`git difftool -d` // то же самое, что и diff, но показывает изменения в заданной difftool.<br>
`git difftool -d master..` // показать изменения, сделанные в текущей ветке.<br>
`git rm <file>` // удалить файл из рабочей директории и добавить в индекс информацию об удалении (зеленые коммиты).<br>
`git rm --cached <file>` // удалить файл из репозитория, но сохранить его локально (красные коммиты).<br>
`git reset` // убрать изменения из индекса коммита, сами изменения останутся.<br>
`git reset <commit/tag>` // отменить все коммиты после указанного коммита, изменения будут сохранены локально.<br>
`git reset --hard <commit>` // принудительно вернутся к указанному коммиту, не сохраняя историю и изменения.<br>
`git reset <file>` // убрать файлы из индекса коммита (изменения не теряются).<br>
`git reset .` //  убрать изменения из индекса всех коммитов, сами изменения останутся (зеленые коммиты).<br>
`git reset --soft / --hard HEAD^1` // отменить последний коммит с сохранением изменений / без сохранения.<br>
`git cherry-pick <commit>` // копирование коммита в другую ветку.<br>
`git reflog --date=iso` // журнал ссылок с отображением даты (.git/logs/refs/heads/. и .git/logs/HEAD).<br>
`git stash` // положить во временное хранилище все отслеживаемые файлы.<br>
`git stash pop` // восстановить последние файлы, положенные во временное хранилище.<br>
`git stash list` // список всех сохраненных изменений во временном хранилище.<br>
`git stash drop` // удалить последние файлы, положенные во временное хранилище.<br>
`git stash apply` // применить изменения к рабочей копии, не удаляя их из набора отложенных изменений.<br>
`git stash clear` // удалить все наборы отложенных изменений.<br>
`git rebase -i` // переместить ветку в начало другой ветки в интерактивном режиме (--interactive).<br>
`git rebase --onto <newBase> <oldBase>` // переместить ветку начиная с определенного коммита.<br>
`git revert <commit>` // отмена изменений коммита и добавление нового коммита с изменениями (диапазон 88a853a^..72f4ed9).<br>
`git restore --staged .` // убрать все из stage (зеленые коммиты).<br>
`git status` // полный список изменений файлов, ожидающих коммита.<br>
`git status -s` // краткий вид изменений.<br>
`git ls-files --other --ignored --exclude-standard` // список всех игнорируемых файлов.<br>
`git log` // список изменения текущей ветки.<br>
`git log --follow <file>` // список изменения текущего файла, включая переименования.<br>
`git log --pretty=format:"%h %s" --graph` // изменение вида отображения истории изменений.<br>
`git log --author='Name' --after={1.week.ago} --pretty=oneline --abbrev-commit` // посмотреть над чем работал заданный пользователь последнюю неделю.<br>
`git log --no-merges master..` // посмотреть историю изменений только для текущей ветки.<br>
`git show <commit>` // показать метадату и изменения в заданном коммите.<br>
`git show <branch>:<file>` // посмотреть на файл в другой ветке, не переключаясь на неё.<br>
`git remote` // посмотреть список доступных удаленных репозиториев.<br>
`git remote -v` // посмотреть детальный список доступных удаленных репозиториев.<br>
`git remote add <remote><url>` // добавить новый удаленный репозиторий.<br>

---

#### Перезаписать локальный репозиторий на удаленный с сохранением данных в новую ветку.<br>
`git checkout master` // перейти на ветку master и обновить ее.<br>
`git branch newBranch` // создать новую ветку.<br>
`git fetch --all` // загрузить последнюю версию файлов с сервера без merge и rebase.<br>
`git reset --hard origin/master` // заменить все локальные файлы на удаленные.<br>
