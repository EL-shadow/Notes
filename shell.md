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
