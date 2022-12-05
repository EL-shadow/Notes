## Вызов Sublime из терминала
`ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl`


## Скрытые файлы
`defaults write com.apple.finder AppleShowAllFiles YES && killall Finder`
`defaults write com.apple.finder AppleShowAllFiles NO && killall Finder`


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
