### Просмотреть текущий конфиг
`git config --list`

### Отменить add
`git reset <file>`

### Втащить изменения в ветке
`git pull --rebase <remote> <branch>`

### Добавить в stage только часть файла
* вызвать с командой `patch`
`git add --patch <file>`
`git add -p <file>`
* Начнется интерактивный add в котором нужно будет выбирать что сделать с hunk
```
Stage this hunk [y,n,a,d,/,j,J,g,e,?]? ?
y - stage this hunk
n - do not stage this hunk
a - stage this and all the remaining hunks in the file
d - do not stage this hunk nor any of the remaining hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help
```

### Переименовать ветку
`git branch -m <oldname> <newname>`

### Переименовать текущую ветку
`git branch -m <newname>`

### Почистить проект от неверсионируемых файлов
`git clean -fdx` (f: force, d: directories, x: ignored files too)

Split a commit in two for the busy ones
Let's see the sequence first before explaining it
```
git rebase -i <oldsha1>
# mark the expected commit as `edit` (replace pick in front of the line), save a close
git reset HEAD^
git add ...
git commit -m "First part"
git add ...
git commit -m "Second part"
git rebase --continue
```

### переключиться на старое состояние
```git reset --hard  oldbranch/v1.65.0```

### Поправить автора
`git commit --amend --author="Author Name <email@address.com>"`

### Delete Remote Branch
`git push origin :<branch_name>`

### Fixup -
`git commit --fixup bbb2222` коммитить с хэшом куда потом фиксапить
`git ci --fixup=bbb2222`
`git rebase --interactive --autosquash origin/dev` переставит коммиты и выставит им fixup вместо pick

### Ветки
`git branch -a` - все ветки
`git branch --merged` - список влитых веток
`git branch --list` - список локальных веток
`git branch -m <newname>` - переименовать ветку
`git branch --merged | egrep -v "(^\*|master|dev)" | xargs git branch -d` - удалить все влитые ветки	


### Если все пропало!
`git reflog`  - да прибудет с тобой git

### или хардкор
* `git fsck --lost-found` - выдаст все потеряные коммиты
* `git show -q bd28a084dd3da42e5c5b60c15ab79a80a4f60a7e` - показать подробности коммита

### все потерянное в читаемом виде (https://stackoverflow.com/questions/30760611/can-i-get-git-fsck-to-show-commit-names)
`git fsck --lost-found | grep "dangling commit" | cut -d" " -f 3 | xargs -I "{}" git --no-pager show --stat "{}"`

### Переименовать в гите
`git mv <old name> <new name>`

### Переименовать чувствительное к регистру
```
git mv casesensitive tmp
git mv tmp CaseSensitive
```

### Если git checkout не удаляет дифф
(https://stackoverflow.com/questions/2016404/git-status-shows-modifications-git-checkout-file-doesnt-remove-them/18792689#18792689)
```
git rm --cached -r .
git reset --hard
```


```
git lfs fetch
git lfs checkout
```


### Отревертить влитое в dev
hash - мерж коммита
```git revert -m 1 <hash>```
