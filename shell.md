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

### Шебанг
`#!` - Шебанг https://ru.wikipedia.org/wiki/%D0%A8%D0%B5%D0%B1%D0%B0%D0%BD%D0%B3_(Unix)
