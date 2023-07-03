## scp
Скопировать локальный файл на сервер:

`scp file.gz root@server.my:/home/dir`

Скопировать всё содержимое папки на сервере (рекурсивно) в локальную папку (с подробным выводом):

`scp -r root@server.my:/home/dir/ /home/local/my/`

Между серверами:

`scp -r root@server1.my:/home/dir/ root@server2.my:/home/dir/`

С указанием порта:

`scp -P 9999 file.zip user@server.my:~/`

Дополнительные флаги
* `-r` - рекурсивное копирование (для директорий)
* `-p` - preserves modification times, access times, and modes from the original file.
* `-C` - использовать сжатие при передачи
* `-P` - порт ssh


## grep
`-r` рекурсивно шариться по папке

`-l` выводить только имена файлов без строки в которой нашлось совпадение

`-L` выводить имена файлов в которых не нашлось совпадение

`-E` - матчить регулярку

`-v` - исключить совпадения

пример отфильтровать из git diff все строки с изменениями и исключить строки где есть слово resolved
`git diff package-lock.json | grep -E "^(\+|-)" | grep -v resolved | less`

## nano
To Search and Replace text in the currently open file:	
* Press Ctrl + \
* Enter your search string [return]
* Enter your replacement string [return]
* Press A to replace all instances


## vim
Для поиска в vim 
* в обычном режиме нужно нажать клавишу "/". 
* Далее необходимо ввести текст, который требуется найти в тексте, и нажать клавишу "Enter". 
	* По-умолчанию, поиск осуществляется в регистрозависимом режиме. Если нужно поискать независимо от регистра, используем Escape-последовательность "\c", например: `/\ccontext` или `/conext\c`
	* Для явного указания регистрозависимого режима, используем Escape-последовательность "\С", например: `/\Сcontext` или `/conext\С`
* Найти следующее вхождение - "n", предыдущее - "N".


## terminal
`> t.txt` - направить вывод консоли в файл t.txt (создать новый или **затереть** существующий)

`>> t.txt` - то же (создать новый или **дописать** в существующий)

`script screen.log` - Начать запись всего вывода терминала в файл `screen.log`
`exit` - Остановить запись

`export PATH="$PATH:./node_modules/.bin"` - добавить алиас для bin из node_modules

`ls -l` - размер файлов

`chmod a+x test.sh` - включить файл на выполнение
`#!/bin/bash` - добавить в начало файла

`source ~/.bash_profile`  - перезагрузить bash_profile

`pbcopy` - скопировать из терминала например `echo test | pbcopy`


## Убить процесс
Ищем процесс processname
`ps | grep -v grep | grep processname | cut -d " " -f1`
Вместо `-f1` может быть `-f2` или `-f3`

Если ок убиваем процесс
`ps | grep -v grep | grep processname | cut -d " " -f1 | xargs kill -9`



## Поиск процесса который залочил порт
`netstat -vanp tcp | grep <port>` <port> например 9229


## Задать пользовательскую переменную в неинтерактивном ssh
On your local client, in your `~/.ssh/config` you can add SetEnv, e.g.
```
Host myhost
  SetEnv FOO=bar
```
Note: Check man ssh_config.

Then on the server, make sure to allow client to pass certain environment variables in your `/etc/ssh/sshd_config` config file:
```
AcceptEnv LANG LC_* FOO BAR*
```
[Источник](https://superuser.com/a/1447790)


## Linux - заполнненость дисков
`df -h` - вывести заполненность по дискам

`du -h --max-depth=1` - вывести вес папок в текущем месте.

`ls -lh` - Есть еще очень полезная опция -h. Она позволяет выводить размеры файлов в списке автоматически в Кб, Мб, Гб и так далее:

`du -sh ./Загрузки/*` - Размеры файлов и папок внутри конкретной папки. Если нужно просмотреть размеры без рекурсивного обхода всех папок, то используется опция -s (--summarize). Также как и с df, добавим опцию -h (--human-readable).
