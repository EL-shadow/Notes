## Shell
### Найти какой порт залочился 
`sudo lsof -i -P | grep LISTEN | grep :$PORT`
[источник](https://stackoverflow.com/questions/4421633/who-is-listening-on-a-given-tcp-port-on-mac-os-x)


## Настройки
## Вызов Sublime из терминала
`ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl`


## Скрытые файлы

* Включить `defaults write com.apple.finder AppleShowAllFiles YES && killall Finder`
* Выключить `defaults write com.apple.finder AppleShowAllFiles NO && killall Finder`


## Скриншоты
Заменить дефолтную папку для скриншотово
`defaults write com.apple.screencapture location ~/Downloads/`

Задать префикс для имен скриншотов
`defaults write com.apple.screencapture name Screenshot_`

Применить изменения: 
`killall SystemUIServer`

## Инфа о продолжительности работы
`uptime` -  время работы вашего компьютера после его последней загрузки и средней нагрузке на него за последние 1, 5 и 15 минут

`ac -p` - общий аптайм вашего МакБука

`last reboot` - список из последних "ребутов" macOS за довольно длительный промежуток времени


`kill -9` SIGKILL https://ru.wikipedia.org/wiki/SIGKILL


## Софт
### iTerm2 настроить поведение
* cmd ,   - Profiles - colors - Color Presets...[Solarized dark] - Minimum contrast 20%
* cmd ,   - Profiles - Keys - add ⌥ ← Action Send Escape sequence Esc+b
* cmd ,   - Profiles - Keys - add ⌥ → Action Send Escape sequence Esc+f
* cmd ,   - Appearance - Panes - uncheck Show per-pane title bar with split panes
* cmd ,   - Profiles - General - Working Directory - Reuse previous session's directory


#### Кодировка в SSH Iterm2
* добавить в ~/.zshrc или ~/.bashrc
`export LC_ALL='en_US.UTF-8'`
