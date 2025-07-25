## Установка Free Download Manager в VoidLinux

### 1. Клонируем void-packages и настройка xbps-src

Клонирование `void-packages` в любую домашнюю директорию и установка окружения для сборки пакетов:
```
$ git clone https://github.com/void-linux/void-packages.git
$ cd void-packages
$ ./xbps-src binary-bootstrap
```

Разрешение сборки пакетов с пометкой "restricted":
```
$ echo XBPS_ALLOW_RESTRICTED=yes >> etc/conf
```

### 2. Клонируем наш репозиторий, собираем и устанавливаем пакет freedownloadmanager

Клонирование репозитория с шаблоном установки `freedownloadmanager` для `xpbs-src`

```
$ cd srcpkgs
$ git clone https://github.com/MrAiupov/freedownloadmanager/
$ cd ../
```

Сборка `freedownloadmanager`
```
$ ./xbps-src pkg freedownloadmanager
```

Установка `freedownloadmanager`

```
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree freedownloadmanager
```

### 3. Обновление пакета freedownloadmanager (при условии что обновлён template в данном репозитории)

Вводим в консоли данные команды, где ранее был клонирован `void-packages`

```
$ cd void-packages
$ cd srcpkgs
$ git clone https://github.com/MrAiupov/freedownloadmanager/
$ ./xbps-src pkg freedownloadmanager
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree freedownloadmanager
```
### 4. Ручное обновление пакета freedownloadmanager

Вы можете сами обновить файл `template`, по которому вы ранее собирали пакет `freedownloadmanager`.

Для начала нужно удостовериться о наличии обновления пакета `freedownloadmanager`.

Нужно перейти по адресу https://www.freedownloadmanager.org/ru/download-fdm-for-linux.htm

И также открыть нашу старую директорию `./void-packages/srcpkgs/freedownloadmanager`, и открыть наш файл `template`

Сверить версию установочного deb файла с сайта, с указанной версией в строке `version` в файле `template`.

И если вышло обновление, скачать данный deb файл с сайта и вычислить хешсумму SHA256 установочного deb файла.

И изменить две строки в файле `template`, это строку `version` указав новую версию (до первого тире) и обновить строку `checksum` указав новую хэшсумму файла, и сохранить файл.

После этого открыть консоль и ввести данные команды, и `freedownloadmanager` обновится до новой версии.

```
$ cd void-packages
$ cd srcpkgs
$ ./xbps-src pkg freedownloadmanager
$ sudo xbps-install -v --repository hostdir/binpkgs/nonfree freedownloadmanager
```

При возникновении вопросов, вы можете их задать в нашем уютном чате по VoidLinux.

https://t.me/voidlinux_ru

Хорошего сёрфинга!
