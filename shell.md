### Рекурсивно пройтись по файлам и найти подстроку
```
grep -r --include "*.txt" texthere .
```
[источник](https://stackoverflow.com/a/8684886/14857550)

### Заменить подстроку в файлах
```
grep -rl oldtext . | xargs sed -i 's/oldtext/newtext/g'
```
[источник](https://stackoverflow.com/a/22385837/14857550)

### Заменить подстроку в файлах которые совпадают по маске

```
grep -rl --include "*.subpath.*" ".commandOld(" . | xargs sed -i 's/\.commandOld(/\.commandNew(/g'
```

### Собрать уникальные строки из текстового файла
```
uniq -u file.txt
```
[источник](https://stackoverflow.com/a/13778360/14857550)

Убедитесь что строки отсортированы, если нет то

```
sort file.txt | uniq -u
```

Если файл большой и сортировка слишком долгая то
```
awk '!seen[$0]++' file.txt
```

### Шебанг
`#!` - Шебанг https://ru.wikipedia.org/wiki/%D0%A8%D0%B5%D0%B1%D0%B0%D0%BD%D0%B3_(Unix)

### TAR заархивировать и распаковать
**Упаковать файл или папку** 
```
tar -czvf name-of-archive.tar.gz /path/to/directory-or-file
```

* -c: сreate 
* -z: сompress the archive with gzip.
* -v: verbose (display progress in the terminal while creating the archive. The v is always optional in these commands, but it's helpful.
* -f: Allows you to specify the filename of the archive.

**Распаковать**
```
tar -xzvf archive.tar.gz
```
* -x: e**x**tract

[источник](https://stackoverflow.com/a/13778360/14857550)

### GZIP
**Упаковать файл ** 
```
gzip -c файл > архив.gz
```

* `-c` - выводить архив в стандартный вывод
* `-d` - распаковать
* `-f` - принудительно распаковывать или сжимать
* `-l` - показать информацию об архиве
* `-r` - рекурсивно перебирать каталоги
* `-0` - минимальный уровень сжатия
* `-9` - максимальный уровень сжатия

**Распаковать**
```
gunzip -c архив.gz
```

Чтобы сжать папку в Linux вам придется сначала заархивировать ее с помощью tar

[источник](https://losst.pro/arhivatsiya-v-linux#gzip)


### CURL
**Скачать курлом как wget**
```
curl http://127.0.0.1:8000 -o outfile
```
Note that curl does not follow redirects by default. To tell it to do so, add -L to the argument list.

[источник](https://stackoverflow.com/a/4572158/14857550)

**Скачать все файылы из списка**
```
curl … $(cat urls.txt)
```
[источник](https://unix.stackexchange.com/a/282143)

```
xargs -n 1 curl -O < your_files.txt
```
[источник](https://serverfault.com/a/722874)

Если нвоые имена файлов нужно явно задать то `curl -o new_file_name.jpg url`

**Переименовать скачанный файл с датой**
```
curl -o prefix-$(date +%H-%M) http://example.com/
```
Например `curl -o $(date +%Y-%m-%d_%H-%M-%S).jpg http://example.com/img.jpg`
[источник](https://stackoverflow.com/questions/37409968/add-timestamp-to-filename-in-curl-command)

### Рекурсивно переименовать файлы с именем по дате создания
```
ls -l -D %Y-%m-%d_%H-%M-%S *.jpg | cut -d " " -f9 -f10 | cat -n | while read n b f; do mv -n  "$f" "$b---$n.jpg"; done 
ls -l -D %Y-%m-%d_%H-%M-%S *.mp4 | tr -s ' ' | cut -d " " -f7 -f8 | cat -n | while read n b f; do mv -n "$f" "$b---$n.mp4"; done
```
По шагам:
1. `ls -l` - выводим список файлов с расширенной инфой о каждом файле
g
2. `ls -l *.jpg` - фильтруем только нужное расширение
3. `ls -l -D %Y-%m-%d_%H-%M-%S *.jpg` - `-D` указываем желаемый формат даты
4. `| cut -d ' ' -f1 ` - сплитим строку по символу разделителю пробел в кавычках и номера желаемых подстрок для вывода, например вхождение 9 `-f9`
5. ` | tr -s ' ' ` - Т.к. `ls` форматирует вывод псевдотабами в несколькими пробелами - заменяем пустые последовательности одним пробелом
6. ` | cat -n` - приписываем порядковый номер к каждой строке
7. `while read n b f;` - перенаправляем подстроки вывода в аргументы `n,b,f`
8. `do mv -n "$f" "$b---$n.jpg";` - непосредственно переименовываем файл, но не затираем при дублировании имен `-n`, с именем `$f` в файл с новым именем, расширение хардкодим чтобы не парсить его из оригинального файла, для этого на шаге 2 и ограничили по расширению.
8.1 `do echo "$f" "$b---$n.jpg";` для тестирования echo

[источник1](https://stackoverflow.com/a/34153342/14857550) [источник2](https://unix.stackexchange.com/a/340069)
