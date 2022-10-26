===Рекурсивно пройтись по файлам и найти подстроку
```
grep -r --include "*.txt" texthere .
```
[источник](https://stackoverflow.com/a/8684886/14857550)

===Заменить подстроку в файлах
```
grep -rl oldtext . | xargs sed -i 's/oldtext/newtext/g'
```
[источник](https://stackoverflow.com/a/22385837/14857550)
