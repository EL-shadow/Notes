### WebStorm
* Исправить автоимпорт
	* Недостающие пробелы `WebStorm -> Preferences -> Editor -> Code Style -> TypeScript -> Spaces (second tab)`, scroll to section `"Within"` and check `ES6 import/export braces`. 
	* Одинарные кавычки в автоимпорте `WebStorm -> Preferences -> Editor -> Code Style -> TypeScript -> Punctuation` 
	включить `Use [single] quotes [in new code]`
* Открывать файл в гитхабе прям из webstorm
	* Найти в настройках keymamp `Open on GitHub` - добавить горячие клавиши
	* залогиниться в гитхабе через интерфейс WebStorm, например главное меню `VCS -> import into Version Control -> Share project on GitHub` - появится окно залогина, после успешного логина webstorm скажет что проект уже на гитхабе есть, нужно отменить импорт.
	* В панели файлов проекта в конекстном меню на файле появится Open on GitHub и хоткей станет рабочим, если remote несколько то оно будет предлагать возможность в каком нужно открыть.
