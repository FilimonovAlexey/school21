## Подготовка к бассейну Школы 21
В данном репозитории представлены материалы, собранные при подготовке к бассейну Школы 21 в Новосибирске, а также примеры решения задач на языке С. Задачи никак не связаны с заданиями Школы 21, найдены на просторах интернета. Решения выполнены владельцем репозитория и не являются единственным верным вариантом. Репозиторий писался на основании той информации, которую можно найти и собрать по кусочкам на тех же просторах интернета. Может не являться истинной, т.к. в Новосибирском кампусе обучение может отличаться от Московского и Казанского кампусов.

#### Оглавление <a name="content"></a>
0. [Введение](#intro)
1. [Работа с терминалом](#terminal)
	- [Основные команды навигации в терминале](#termCommand)
	- [Справка о командах](#help)
	- [Прочее](#other)
2. [Устанавливаем и настраиваем vim](#vim)
    - [Работа в vim](#workVim)
	- [Перемещение по файлу](#navigation)
	- [Ввод текста](#enterText)
	- [Удаление и вставка](#deletAndPaste)
	- [Отмена изменений](#undo)
	- [Выход из vim](#quit)
	- [Терминал в vim](#term)
	- [Заголовок школы](#header)
	- [Решение некоторых проблем](#solveProblems)
	- [Дополнительный материал](#addMaterial)
3. [Компилятор gcc](#gcc)
	- [Как компилировать](#compiling)
4. [Устанавливаем и настраиваем norminette](#norminette)
5. [Работа с git](#git)
	- [Введение](#gitIntro)
	- [Регистрация на GitHub](#gitHub)
	- [Установка Git](#git_install)
	- [Клонирование репозитория](#git_clone)
	- [Индексация изменений](#git_add)
	- [Коммит изменений](#git_commit)
	- [Отправка изменений в удалённый репозиторий](#git_push)
	- [Pull requests](#pull_requests)
	- [Список благодарных](#contributor)
6. [Hello, World!](#helloWorld)

### Введение <a name="intro"></a>
Если ты нашёл этот репозиторий, то наверняка уже много прочитал различной информации про Школу 21, про франшизу Школы 42, про peer-to-peer (P2P) метод обучения, про бассейн (интенсив) и т.д. и т.п. Скорей всего ты уже прошёл первый отбор: 2 игры, видео-интервью и онлайн встречу. Перед тобой следующий этап - это бассейн. Как раз о нём я и постараюсь рассказать, основываясь на информации, которую смог найти сам. Опишу этапы моей подготовки.

Первое, что нужно понять, - вся работа во время интенсива будет проходить на iMac, компьютерах от Apple. Из чего можно сделать вывод, что в работе будут использоваться bash-команды (но это неточно), может быть ещё установлена zsh-командная оболочка. Командные оболочки позволяют работать в терминале с операционной системой с помощью простых команд без GUI. Прежде всего командные оболочки нужны системным администраторам для работы с серверами, где GUI вообще по факту не нужен. Но и программистам навыки работы с терминалом очень пригождаются в работе. Потому нужно научиться работать с Bash. Один из способов потренироваться, это через терминал дистрибутивов Linux, в которых уже предустановлен Bash. Будете ли вы устанавливать новую ОС, или ставить виртуальную машину, или пользоваться Live-режимом с USB-флешки - это решать вам.  

Второе - языком программирования интенсива является язык Си. Да, язык не самый популярный у новичков и не прост в понимании для начинающих. Но таковы правила Школы 21, начинать с азов. Это компилируемый статически типизированный язык программирования, потому для работы с ним нужен компилятор. По разным источникам в Школе 21 может быть компилятором как Clang, так и gcc. Я для тренировки выбрал gcc.

Третье - текстовые редакторы. На интенсиве, скорей всего, будут доступны только nano, emacs и vim. Советую заранее выбрать один из этих редакторов и научиться в нём работать, чтобы не тратить драгоценное время на интенсиве. Я выбрал редактор vim. Мне так вкусней.

Четвёртое - правила написания кода в Школе 21. Они есть и их нужно соблюдать, иначе можно отхватить 0 баллов за выполнение задания. Да, всё настолько строго, да, для новичков. Существует сдандарт написания кода, которому придерживается Школа 21 (Школа 42). Стандарт можно почитать тут [The Norm](https://cdn.intra.42.fr/pdf/pdf/960/norme.en.pdf). Для проверки соответсвия кода стандарту используется программа Norminette.

Пятое - работа с git. Git - это система управления версиями. У Git две основных задачи: первая - хранить информацию о всех изменениях в вашем коде, начиная с самой первой строчки, а вторая - обеспечение удобства командной работы над кодом. Каждый программист должен уметь пользоваться Git-ом. Именно сейчас вы читаете данный репозиторий на веб-сервисе GitHub, который основан на системе контроля версий Git. На бассейне работа будет завязана на локальном git-репозитории, с помощью git-команд нужно будет отправлять решения на проверку.

И наконец, шестое - первая программа "Hello, World!", на которой я покажу все описанные выше инструменты. 

P.S. Все примеры и команды, показанные мной ниже, я выполнял в терминале дистрибутива Linux Mint 20.1 MATE в командной оболочке Bash. 

[Оглавление](#content)

### 1 Работа с терминалом <a name="terminal"><a>

Под терминалом принято понимать окружение, где можно вводить команды и получать на них ответ, это может быть физический терминал или терминал на компьютере.

Запуск терминала в Linux Mint осуществляется сочетаниями клавиш:

	Ctrl + Alt + T

Запуск терминала в macOS по умолчанию сочетанием клавиш не осуществляется.

Можно запустить из поиска Spotlight

	Command(⌘) + пробел

Во всплывающем окошке введите слово «Терминал» (terminal). После того, как увидите нужное приложение, просто кликните на него.

Другой способ запуска терминала в macOS - через Launchpad
Вызвать Launchpad можно нажатием

	F4

По умолчанию терминал находится в папке "Другие"

Во всплывающем окошке введите слово «Терминал» (terminal). После того, как увидите нужное приложение, просто кликните на него (не проверял).

Так выглядит терминла в Linux Mint:
![Terminal](https://i.ibb.co/162pmwD/terminal.png)

[Оглавление](#content)

**Основные команды навигации в терминале:** <a name="termCommand"></a>

Узнать, в какой рабочей папке вы находитесь:
```
$ pwd
```
Вывести список файлов и каталогов в рабочей папке:
```
$ ls
```
Вывести список файлов и каталогов в рабочей папке, включая скрытые:
```
$ ls -a
```
Вывести список файлов и каталогов с полной информацией о них в рабочей папке, включая скрытые:
```
$ ls -all
```
Команда cd используется очень часто при работе с папками в терминале. Она позволяет сменить текущую папку на произвольную. Можно использовать чтобы не набирать длинные пути, также она необходима при компиляции. По умолчанию, текущая папка - домашняя.

Перейи в подпапку домашней папки:
```
$ cd Загрузки/
```
Вернуться в предыдущую папку:
```
$ cd -
```
Перейти в родительский каталог:
```
$ cd ..
```
Быстрый переход в домашнюю папку:
```
$ cd
```
Создание файла в рабочей папке:
```
$ touch file_name.expansion
```
Создание каталога в рабочей папке:
```
$ mkdir dir_name
```
Удаление файла в рабочей папке:
```
$ rm file_name
```
Удаление каталога и рекурсивно всё его содержимое:
```
$ rm -r dir_name
```
Переименовать файл:
```
$ mv file_name file_new_name
```
Переместить файл в другой каталог:
```
$ mv file_name dir_name/
```
Копировать файл в рабочую папку:
```
$ cp file_name copy_file_name
```
Копировать каталог в другой каталог:
```
$ cp -a dir_name_1/ dir_name_2/
```
Копировать файл в каталог:
```
$ cp frile_name dir_name/
```

[Оглавление](#content)

**Справка о командах** <a name="help"></a>

Если не знаешь, как работает команда и её параметры, спроси у "мужика" (man - сокращение от manual - инструкция):
```
$ man cp
$ man ls
$ man mkdir
...
```
Чтобы узнать о параметрах команды, используйте параметр `--help`:
```
$ ls --help
$ cd --help
$ rm --help
...
```

[Оглавление](#content)

**Прочее** <a name="other"></a>

Команда `bg` (сокращение от background - фон) позволяет посмотреть процессы, которые выполняются в фоне. Если вы нажмете сочетание клавиш `Ctrl+Z`, то утилита будет свернута в фоновый режим (такое может случиться при работе в vim). Этой командой вы можете посмотреть последний свёрнутый процесс и его id для данной оболочки.
```
$ bg
```
Посмотреть все запущенные процессы, которые работают на заднем фоне:
```
$ jobs
```
Эта команда позволяет восстановить процесс из фона, в параметрах ей нужно передать только идентификатор нужного процесса, который вы можете узнать с помощью `bg` или `jobs`.
```
$ fg id_process
```
[Оглавление](#content)

### 2 Устанавливаем и настраиваем vim <a name="vim"><a>

**Vim** (сокр. от **V**i **Im**proved, произносится «вим») — свободный текстовый редактор, созданный на основе более старого vi. Ныне это мощный текстовый редактор с полной свободой настройки и автоматизации, возможными благодаря расширениям и надстройкам. Пользовательский интерфейс Vim’а может работать в чистом текстовом (консольном) режиме.

Прежде чем устанавливать vim, необходимо обновить базы данных пактов (необязательно), чтобы установить последнюю версию vim:
```
$ sudo apt update
```
Установка vim:
```
$ sudo apt install vim
```
Узнать версию vim, также выводит информацию о пользовательсом файле vimrc, он нам понадобиться для настройки vim:
```
$ vim --version
```
Открыть туториал по vim:
```
$ vimtutor
```
Создать файл через vim в рабочей папке:
```
$ vim file_name.expansion
Пример:
$ vim main.c
```

[Оглавление](#content)

#### Работа в vim <a name="workVim"></a>

**Основные режимы работы**

*Обычный режим* - перемещение по файлу, стирание текста и другие редактирующие функции. Это - основной режим, только из него можно сразу перейти в другие режимы. Для возврата в основной режим из любого другого режима:

	ESC, иногда 2 раза
	Ctrl + [

*Режим ввода* - ввод текста. Как только завершается ввод текста, принято сразу возвращаться в обычный режим. Заметьте, что стирание и ввод текста происходит в двух разных режимах. Переход в него из обычного режима:

	i
	Insert

*Командный режим* - команды (операции с файлом, поиск и замена, настройка редактора…). Переход в него из обычного режима:

	Shift + :

*Режим поиска* - ввод поискового запроса. Переход в него из обычного режима:

	/ , поиск от курсора до конца документа
	? , поиск от курсора до начала документа
	n - повторить поиск
	N - повторить поиск назад

*Визуальный режим* - режим выделения текста:

	v + влево или вправо стрелками
	Shift + v , вся строка целиком
	Ctrl + v , выделение прямоугольником часть текса

[Оглавление](#content)

**Перемещение по файлу** <a name="navigation"></a>

Команды, которые использую я (их может быть достаточно для комфортной работы в vim, больше команд можете найти в `vimtutor` ):

	Для перемещение курсора можно использовать стрелки вверх, вниз, вправо и влево (см. рисунок ниже)

![Стрелки](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Flinchakin.com%2Ffiles%2Fword%2F1000%2F15%2F1.jpg&f=1&nofb=1)

	Ctrl + f - перейти на сраницу (экран) вниз
	Ctrl + b - перейти на страницу (экран) вверх
	0 ("ноль") - перейти в начало текущей страки
	$ - перейти в конец текущей строки
	Ctrl + стрелка вправо - перейти на слово вправо
	Ctrl + стрелка влево - перейти на слово влево
	Shift + } - перейти на абзац вниз
	Shift + { - перейти на абзац вверх
	gg - перейти в начало файла
	G - перейти в конец файла
	number + G - перейти на конкретную строку number
	
**Ввод текста** <a name="enterText"></a>

Следующие команды переводят редактор в режим ввода:

	i - перейти в режим в ввода с текущей позиции
	I - переместиться в начало строки и перейти в режим ввода
	A - переместиться в конец строки и перейти в режим ввода
	S - удаляет всю текущую строку и переходит в режим ввода

**Удаление и вставка** <a name="deletAndPaste"></a>

	x - удалить символ под курсором вправо;
	X - удаляет символ влево;
	dd - вырезать текущую строку;
	C - удаляет текст с екущего положения курсора до конца строк и переходит в режим ввода
	yy или Y - копирование текущей строки в буфер
	y - копирование выделенной строки в буфер
	p - вставка содержимого буфера под курсором
	P - вставка содержимого буфера перед курсором
	J - слияние текущей строки со следующей

**Отмена изменений** <a name="undo"></a>

	u - отмена последней команды
	Ctrl + r - вернуть последние изменения 

**Выход из vim** <a name="quit"></a>

Наконец, дошли до самого интересного, выхода из редактора vim, который является проблемой для новичка:

	:q! - выйти без сохранения
	:wq - записать файл и выйти
	ZZ - записать файл и выйти (если файл не изменяли, то записи не будет)

**Терминал в vim** <a name="term"></a>

В vim можно открыть терминал, что позволяет удобно одноврменно писать код и компилировать:

	:term - открыть терминал в vim
	Ctrl + w - переключаться между окнами

[Оглавление](#content)

**Заголовок Школы 21 (Школы 42)** <a name="header"></a>

Во всех файлах должен быть заголовок (heder), который установлен правилами Школы (см.на рисунке ниже).

![Header](https://i.ibb.co/h8Xsxnv/header.png)

Для создания заголовка 42header необходимо использовать плагин, который скачивается и устанавливается с помощью пакетного менеджера Vundle.

> Плагин нужен только тем, кто работает на своём пк/ноутбуке. На компьютерах школы всё и так прекрасно работает.

Чтобы скачаь Vundle, понадобиться установить систему контроля версий Git (как им пользоваться, рассказываю  ниже):

	$ sudo apt install git

Теперь создадим необходимую директорию и скачаем туда менеджер Vundle:

	$ mkdir -p ~/.vim/bundle
	$ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim

Далее настраиваем Vim и пактный менеджер Vundle, а также запишем в очередь на установку плагин 42header. Для этого создадим в каталоге ~/.vim файл vimrs:

	$ cd .vim/
	$ vim vimrc

Был созда и сразу открыт в редакторе vim файл vimrc, в который необходимо записать следующие настройки:

	set number
	set cursorline
	set cursorcolumn
	set autoindent
	set cindent
	highlight ExtraWhitespace ctermbg=red guibg=red
	match ExtraWhitespace /\s\+$\|\s+\s{1}/
	highlight MoreThan80 ctermbg=blue guibg=blue
	:2match MoreThan80 /\%81v.\+/
	set tabstop=4
	set shiftwidth=4

	set nocompatible
	filetype off
	set rtp+=~/.vim/bundle/Vundle.vim
	call vundle#begin()
	Plugin 'VundleVim/Vundle.vim'
	Plugin 'pandark/42header.vim'
	
	" Add plugins here

	call vundle#end()
	filetype plugin indent on

> Не забываем сохранить изменения и выйти из vim командой `:wq`.

Теперь необходимо установить и обновить прописанные в vimrc плагины. Откройте vim и выполните в нём команду:

	$ vim
	:PluginInstall

Пропишем в файле настроек командной оболочки имя пользователя $USER и почту $MAIL для нашего заголовка 42header. Открываем .bashrc (или .zshrc, если у вас zsh): 

	$ vim .bashrc

и прописываем вконце строки:

	export USER=тут_будет_ваш_login
	export MAIL=тут_будет_ваш_email

После сохранения .bashrc, его необходимо перезапустить:

	$ source .bashrc

Проверяем. Запускаем vim и прописываем команду:

	:FortyTwoHeader

Чтобы поменять команду с `:FortyTwoHeader` на команду `:Stdheader`, изменим строку 187 в:

	$ vim ~/.vim/bundle/42header.vim/plugin/42header.vim

на:

	command! Stdheader call s:fortytwoheader()

Чтобы сделать печать заголовка при нажатии на кнопку `F5`, пропишем в файле vimrc:

	nmap <f5> :Stdheader<CR

[Оглавление](#content)

**Решение некоторых проблем** <a name="solveProblems"></a>

Не работает кнопка `Backspace`.
Откройте vim и пропишите команду:

	:set backspace=indent,eol,start

**Дополнительный материал** <a name="addMaterial"></a>

Другие настройки vim:
[Настройка vim](https://losst.ru/nastrojka-vim)

Установка цветовой схемы Drakula:
[Drakula](https://draculatheme.com/vim)

Так выглядит цветовая схема Drakula:
![Цветовая схема Drakuls](https://i.ibb.co/Z2zFmfL/Dracula.png)

Выбор встроенных в vim  цветовых схем:
```
:colorscheme + Tab
```

Узнать текущую цветовую схему:
```
:color
```

[Оглавление](#content)

---
### 3 Компилятор gcc <a name="gcc"><a>

Как я уже говорил выше, на бассейне в Школе 21 могут быть два компилятора: Clang или gcc. Я решил готовиться на gcc.

Обновляем данные о пакетах, это можно не делать, если делали до этого:
```
$ sudo apt update
```

Устанавливаем gcc:
```
$ sudo apt install gcc
```

Проверяем версию компилятора:
```
$ gcc --version
```
У меня установилась версия 9.3.0.

**Как компилировать** <a name="compiling"></a>

Компилируем наш код:
```
$ gcc -Wall -Wextra -Werror file_name.c -o exe_file_name
```
Выполнять команды нужно в каталоге, в котором находится файл с вашим кодом `faile_name.c`. В этом же каталге будет создан исполняемы файл с именем, которое вы сами придумаете `exe_file_name`.

`-Wall` - это "агрегатор" базовых предупреждений.

`-Wextra` - "агрегатор" дополнительных предупреждений. Включает много интересного, чего нет в -Wall0.

`-Werror` - данный флаг делает все предупреждения ошибками. Код не скомпилируется при наличии хотя бы одного предупреждения.

Эти команды помогут выявлять ошибки в коде, которые вы могли допустить.

`-o` - задает имя выходного файла.

Если после выполнения команды, появились надписи об ошибках, то необходимо их устранить (исправить код) и снова запустить команду копиляции. После того, как всё исправили и компиляция прошла успешно, можно запустить исполняемый файл.
```
$ ./exe_file_name
```

[Оглавление](#content)

---
### 4 Устанавливаем и настраиваем Norminette <a name="norminette"><a>

Для работы с Norminette нам поребуется установить Python 3 и pip. pip - это инструмент, который позвляет устанавливать и управлять библиотеками и модулями в проектах на Python.

Устанавливаем Python 3:
```
$ sudo apt install python3.8
```

Вместо `python3.8` может быть любая версия, но для работы Norminette требуется версии 3.7+ (3.7, 3.8, 3.9).

Проверяем версию установленного python3:
```
$ python3 -V
```
Устанавливаем инструмент pip:
```
$ sudo apt install -y python3-pip
```
Проверяем версию pip:
```
$ pip -V
```
У меня установилась версия 21.1.2.

Устанавливаем Norminette:
```
$ python3 -m pip install norminette
```
Обновляем до последней версии:
```
$ python3 -m pip install --upgrade norminette
```
Для удобной работы с Norminette добавим пару `alias` в файл .bashrc или .zshrc. Откроем файл .bashrc в домашней декриктории:
```
$ vim .bashrc
```
В самом низу добавляем две строчки:
```
alias norminette="~/.local/bin/norminette"                                     
alias norm="python3 ~/.local/bin/norminette"
```
Сохраняем изменения и перезапускаем .bashrc:
```
$ source ~/.bashrc
```
Теперь Norminette можно вызывать bash-командой `norminette` или `norm`. Проверяем версию Norminette:
```
$ norminette -v
```
или
```
norm -v
```
Чтобы проверить ваш код через Norminette, в катологе, в котором находится файл с вашим кодом, вводим следующую команду:
```
$ norm file_name.c
```
Если выдаёт сообщение `OK!`, значит код написан правильно, иначе будут сообщения о различных ошибках.

Описание ошибок можете прочитать тут: [Ошибки в коде](https://42-21-school.blogspot.com/2019/07/main.html)

[Оглавление](#content)

---
### 5 Работа с Git <a name="git"><a>

**Введение** <a name="gitIntro"></a>

Я долго размышлял, что в этой главе рассказать, на что сделать упор и т.д. и т.п. Рассказать только о тех функциях, которые могут пригодиться на бассейне? Это не даст целостной картины о таком важном для программистов иснтрументе, как Git. Если затрагивать только Git без онлайн-репозиториев, то опять же новички (я тоже новичок :wink: ) не поймут полезность этого интсрумента.

Постараюсь рассказать так, чтобы каждый имел минимальное представление о Git, показать некоторые действия, повторив которые, у вас появится небольшая пратика по Git и вы сможете внести свой вклад в развитие данного мини-проекта, стать одним из его разработчиков. И вам полезно, и мне приятно. :blush: :pray: Повторив действия, описанные в данной главе, вы получите опыт работы с Git, тренировку, которая поможет вам на бассейне. Удачи вам!

Что же такое Git? Как говорит нам интеренет, Git - это распределённая система контроля версий, которая позволяет записывать изменения в файл или набор файлов в течение времени и предоставляет возможность вернуться позже к определённой версии. На практие Git - это консольная утилита, работа которой основана на консольных командах, но существуют программы с графическим интерфейсом по работе с Git. [10 лучших GUI-клиентов Git для разработчиков](https://techrocks.ru/2020/04/24/best-git-gui-for-mac-linux-windows/)

Не стоит путать Git c GitHub:

Git | GitHub 
--- | ---
программа, которую нужно устанавливать и подключить к проекту для управления системой контроля версий | сайт-хранилище для историй версий проектов
самая популярная система контроля версий | самое популярный онлайн-репозиторий
![Git](https://i.ibb.co/CzJmYG7/Git.png) | ![GitHub](https://i.ibb.co/F8TKng4/GitHub.png)

Git и GitHub настроены на взаимодействие, потому часто используются, как единый механизм работы с проектом.

На бассейне будет примерно такой же механизм, только вместо GitHub будет подобный локальный репозиторий, данные которого хранятся на серверах Школы 21 (моё предположение). Доступ к такому репозиторию будет даваться только на компьютерах Школы. Но для подготовки к бассейну нам будет достаточно Git и GitHub. Конечно, помимо GitHub есть другие подобные хранилища, но как мы уже поняли выше, GitHub является самым популярным из них.

Сейчас я буду объяснять некоторые инструменты GitHub, но буду приводить аналогию, которая может встретиться на бассейне. Надеюсь, это поможет спокойно плавать.

[Оглавление](#content)

**Регистрация на GitHub** <a name="gitHub"></a>

Для начала, нужно создать аккаунт и зарегистрироваться на сайте GitHub. [GitHub Sign Up](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home)

Заполняем поля: электронная почта; пароль; имя пользователя (по нему будут искать ваш репозиторий); ставим метку `y` или `n`, если хотим или не хотим получать новости на почту (см. картинку ниже).

![Welcome to GitHub!](https://i.ibb.co/p14bhV1/1-GitHub.png)

Проходим верификацию пользователя, нужно выбирать элемент пазла (у меня так было). Затем нужно будет подтвердить свою электронную почту.

![Link inside](https://i.ibb.co/tqfr6nC/2-GitHub.png)

Ищем на указанной вашей электронной почте письмо от GitHub и подверждаем свою почту:

![Check email](https://i.ibb.co/pRZVf3F/3-GitHub.png)

После чего перекидывает на стартову страницу GitHub нового авторизованного пользователя, где вам предлагают создать новый репозиторий, организацию или изучить гайд по GitHub.

![First page](https://i.ibb.co/BKHqCdQ/4-GitHub.png)

> Этого этапа на бассейне, скорей всего не будет. Нам сразу дадут логин и пароль, по которым сможешь входить в систему Школы 21. Вличном кабинете будут ссылки на созданные для нас репозитории.

Итак, когда у вас есть свой аккаунт на GitHub, вы можете начать с ним работать: создавать свои репозитории, клонировать репозитории других разработчиков и даже принимать участие в разработке открытых проектов. Как раз мы этим и займёмся. Вы сможете принять участие в разработке этого самого ресурса, которой сейчас и читаете.

Вы могли заметить, что в тексте есть некоторые очепятки (которые, возможно, оставил специально), неточности, или вообще информация уже устарела. Заметили? Тогда приступайте к выполнению следующих пунктво ниже.

[Оглавление](#content)

**Установка Git** <a name="git_install"></a>

Установим Git на наш ПК.

Для macOS. Открываем терминал и прописываем команду:

Если установлен Homebrew

	$ brew install git

Если нет, то вводим эту команду

	$ git --version
	После этого появится окно, где предложит установить Command Line Tools (CLT).
	Соглашаемся и ждем установки. Вместе с CLT установиться и git.

Для Linux. В терминале прописываем команду:

	$ sudo apt install git

На этом установка Git завершина. Чтобы проверить, прошла ли установка успешно, пишем команду:

	$ git --version

Должна появиться информация о версии Git.

> Данного этапа на бассейне не будет, т.к. Git уже должен быть установлен на всех ПК Школы 21.

[Оглавление](#content)

**Клонирование репозитория** <a name="git_clone"></a>

Зайдём на страницу репозитория [@robotrainer/school21](https://github.com/robotrainer/school21) и нажмём на кнопку `Fork` в правом верхнем углу:

![Fork](https://i.ibb.co/vk29GLp/Fork.png)

После нажатия кнопки вы автоматически переместитесь уже в свой репозиторий, который будет выглядеть точно так же, как и тот, что вы только что "форканули". Слева вверху будет написан ваш `username` и название репозитория, под ними `forked from robotrainer/school21`, а справа вверху кнопка `Fork` будет уже не доступно, а число увеличиться на 1. Это означает, что вы создали свою ветку существующего чужого репозитория и можете стать одним из его разработчиков.

![Forked from](https://i.ibb.co/f1cG4XB/Fork-2.png)

Теперь, чтобы вы могли редактировать свой репозиторий, необходимо создать на вашем ПК дерикторию, куда клонируем даный репозиторий. В терминале (напомню, что мы мы работаем на Linux ОС или macOS) пропишем следующие команды в домашней папке или в любой другой, где вам удобно:

	$ mkdir project

Переходим в созданную дерикторию и клонируем туда наш репозиторий:

	$ cd project/
	$ git clone https://github.com/git_username/school21.git

Ссылку по которой будет происходить клонирование репозитория можно найти на стриничке репозитория:

![git clone](https://i.ibb.co/Ykqxyhn/git-clone.png)

Если сделали всё верно, то в каталоге `project` должен появиться каталог с названием репозитория `school21`, в котором будут находиться клонированные файлы репозитория, доступные для редактирования.

![terminal](https://i.ibb.co/nmxFgz9/terminal-git-clone.png)

Не стоит забывать, что владелец репозитория, который вы "форканули", тоже может вносить изменения в основную ветку репозитория. В вашей же ветке эти изменения автоматически не появятся, нужно их добавлять вручную. Сделать это можно через GitHub, он сам вам подскажет, что в основной онлайн-ветке были изменения и предложит их извлечь и слить с вашей онлайн-веткой. Таким образом, в вашей онлайн-ветке появятся новые изменения/обноления (см. картинку ниже).

![Fetch and merge](https://i.ibb.co/Q6PT7Xc/Fetch-and-merge.png)

После этого данные в вашем онлайн-репозитории обновятся, и нужно эти обновления добавить в ваш локальный репозиторий на ПК.
Для этого нужно зайти в дерикторию `~/project/school21/` и ввести там следующую команду:

	$ git pull origin master

Где `origin` название сервера (удалённая ветка) онлайн-репозитория, `master` - ваша локальная ветка. Команда извлекает изменения `origin` и `master`, объединяет и записывает их в `master`. После выполнения команды, нам показывают, сколько изменений было добавлено и сколько удалено. Клонирование оба имени `origin` и `master` настраивает автоматически.

![Pull](https://i.ibb.co/K6rTbwD/pull.png)

Важность этой процедуры в том, что вы не сможете добавить свои изменения в основную ветку онлайн-репозитория другого разработкчика, пока у вас локально не будут иметься последние обновления этой самой осноной векти. Запутано всё и сложно понять, да. Но так работает Git. Потому следите за обновлениями основной ветки.

> Данный этап будет на бассейне, только ссылка на клонирование репозитория будет выглядить по-другому, т.к. вместо GitHub будет другой удалённый репозиторий. Процедура клонирования будет такая, как и тут. Т.е. перед решение задачи, вы должны клонировать удалённый репозитория себе на ПК. В клонированной папке вы и создаёте файлы с решением задания.

[Оглавление](#content)

**Индексация изменений** <a name="git_add"></a>

Теперь у нас есть файлы, которые мы можем редактировать, удалять, добавлять и т.д. Самый простой способ, это отредактировать файл README.md, в котором, кстати, вся эта писанина и содержится. Открываем README в vim (вы же уже умеете в нём работать), при этом вы должны находиться в дриктории, где и лежит сам README.md проекта:

	$ vim README.md

![vim readme.md](https://i.ibb.co/Wpdm2mK/README.png)

В открывшмся документе введите команду `/Ткни` - это команда поиска по ключевому слову `Ткни`, и нажмине `Enter`. Вас переместит на строчку спойлера `Ткни сюда и увидишь список`. На следующих строчках вы увидете список тех, кто уже проделал все пункты ниже до вас и отплагодарил автора статья, т.е. меня. Создаёте новую строчку со следующим порядковым номером и впишите туда свой `username` GitHub, чтобы тоже внести свой вклад. У меня это номер 1. А какой у тебя?)

![Contributor](https://i.ibb.co/pysHnVP/Contributor.png)

Затем вводим команду `:wq` - сохраняем и закрываем vim. Теперь нам необходимо проиндексироваь изменения файла в git. Для этого вводим следующую команду в терминал:

	$ git add README.md
	
Этой командой мы указываем индексацию конкретного файла **README.md**, не учитывая другие файлы, даже если они тоже были изменены. Если мы хотим учесть все изменения во всех файлах текущей дериктории, то используют `git add .`. Если хотим учесть изменения все изменения во всех файлах текущей дериктории и соседней дериктории, то используют `git add -A` или `git add --all`.

![git add](https://i.ibb.co/MsHZdd3/git-add.png)

Команда `git status` позволяет определить, какие файлы в каком состоянии находятся.

> Важный момент! Если вы после выполнения команды `git add` снова измените файл, то эти изменения не попадут в индексацию изменений. Вам снова придётся выполнять команду `git add`, чтобы проиндексировать последнюю версию файла.

> Данный этап будет на бассейне. После создания, редактирования файла с решением его обязательно нужно индексировать.

[Оглавление](#content)

**Коммит изменений** <a name="git_commit"></a>

После индексации изменений необходимио зафиксировать изменения - сделать коммит. Важно, любые изменения, добавления файлов или удаления, которые произошли после `git add` или файлы, для которых вы не выполняли `git add`, не попадут в этот коммит. Эти файлы остануться измененными только на вашем ПК. Для фиксации изменений выполните следующую команду:

	$ git commit -m "ваш комментарий к коммиту"

Параметр `-m` позволяет вводить комментарий к комммиту в ковычках. Комментарий должен содержать минимальное возможное количество символов и отражать суть коммита.

![git commit](https://i.ibb.co/74qbtfs/git-commit.png)

Можно ещё раз выполнить команду `git status`, чтобы посмотреть состояние файлов. Посмотреть историю коммитов можно командой `git log`.

> Этот этап будет на бассейне. После индексации файла с решением нужно зафиксировать изменения коммитом.

[Оглавление](#content)

**Отправка изменений в удалённый репозиторий** <a name="git_push"></a>

Следующий этап - отправка изменений в удалённый репозиторий на GitHub. Для этого выполните команду:

	$ git push origin master

Вас попросят ввести логин пользоателя и пароль. Команда `push` отправляет вашу ветку `master` с ПК на сервер `origin` на GitHub. Напомню, что клонирование настраивает имена `master` и `origin` атоматически.

![Git push](https://i.ibb.co/Tcn4DWB/git-push.png)

Когда вы откроете свою ветку репозитория на GitHub, то увидете, что там появилась строча о том, что ваша ветка опережает основную ветку репозитория другого человека на 1 коммит. Напротив редактированного файла README.md появится ваш комметарий к коммиту.

![Update](https://i.ibb.co/BNZVjsG/update.png)

> Этот этап тоже будет на бассейне и он очень важен! В бассейне эта команда будет не просто отправлять и сохранять файл в удалённый репозиторий, но и проверять на првильность выполнения задания, т.е. команду `git push` для конкретного задания можно будет сделать только **один раз**. После пуша задание будет проверенно и система должна выдать количество баллов за выполнение. После этого этапа попытки изменить файл и снова его запушить будут бессмыслены. Потому будьте очень внимательны!

[Оглавление](#content)

**Pull requests** <a name="pull_requests"></a>

Данный этап не относится к бассейну. Здесь я покажу, как отправить вашы изменения в репозиторий другого человека. Все действия будут проходить на ресурсе GitHub.

После того, как вы запушили (выполнили `git push`) свои изменения в свой онлайн-репозиторий, теперь можно попросить владельца основной ветки онлайн-репозитория слить с вашей изменённой веткой онлайн-репозитория. Когда вы откроете страничку своего онлайн-репозитория, то увидете, что там появилась строчка, что ваша ветка опережает родительскую ветку на 1 коммит. Емли нажать на `Contribute`, появится всплывающее окно с кнопкой `Open pull request`.

![Pull request](https://i.ibb.co/K6Vq9n1/pull-request.png)

Откроется страница сравнения изменений на которой необходимо нажать на кнопку `Create pull request`. Таким образом вы создаёте запрос на втягивание изменений с вашей ветки в ветку репозитория другого человека.

![Create pull request](https://i.ibb.co/bL0DR14/create-pull-request.png)

Откроется форма, в которой вверху оставляете комментарий к коммиту, внизу пояснение для владельца репозитория, кому вы отправялете запрос на втягивание изменений.

![Open a pull request](https://i.ibb.co/kgvxDpZ/Open-a-pull-request.png)

Дальше появится информация о том, что запрос отправлен и ваша ветка не имеет конфликтов с основной родительской веткой.

![Can merge pull requests](https://i.ibb.co/1rZ1hKc/image.png)

> На этом этапе ваша работа закончена. Вы успешно клонировали репозиторий другога человека, внесли в него изменения, индексировали их, зафиксировали и отправили в свой репозиторий. Затем создали и отправили предложение на слияние ваших изменений с основной родительской веткой репозитория дрйгого человека. Вам остаётся только ждать реакцию от владельца основной ветки, примет ли он ваше предложение или временно отклонит, сообщив вам, что нужно ещё отредактировать, прежде чем ваши изменения можно принять.

Давайте посомтрим, какие нужно сделать действия владельцу оснвной ветки для принятия предложенных вами изменений. Владелец основной ветки, зайдя на страничку своего репозитория, видит, что появился новый `Pull requests`. Нажав на эту вкадку, он увидит предложенный коммит другим пользователем GitHub.

![Pull requests](https://i.ibb.co/fCy9qz1/image.png)

Нажав на этот коммит, откроется страница с формой комментария коммита, в которой можно оставить благодарность за вклад или другие любые коментарии, касающиеся коммита. Если предложенные изменения устраивают владельца основной ветки, он может нажать на кнопку `Merge pull request`.

![Merge pull request](https://i.ibb.co/f2ddkQk/Merge-pull-request.png)

Наблюдаем, что комментарий добавлен и можно подтвердить слияние веток.

![Confirm merge](https://i.ibb.co/JCbRvfz/Confirm-merge.png)

После этого, перейдя на основную страницу репозитория, владелиц основной ветки увидит надпись о слиянии с веткой от другого пользователя и коммит напротив изменённого файла. Исследовав изменённый файл README.md, можно найти новые добавленные строчки.

Информация о слиянии веток | Принятые изменения
--- | ---
![merge](https://i.ibb.co/pXhW7VV/image.png) | ![update](https://i.ibb.co/kqwWx1H/image.png)

> Так выглядит пример совместной разработки на ресурсе GitHub. Вы можете попробовать внести свой вклад в развитие не только данного репозитория, но и во множество других открытых проектах. Это поможет вам набраться опыта работы с git, GitHub и в совместной разработке.

[Оглавление](#content)

**Список благодарных** <a name="contributor"></a>

<details>
<summary>Ткни сюда и увидишь список:</summary>

1. robotraine 
2. ...
3. ...

</details>

[Оглавление](#content)

---
### 6 Hello, World! <a name="helloWorld"><a>

Тут я расскажу, как можно вывести на экран стандартную надпись первой программы `Hello, World!`, не используя заголовочного файла `stdio.h` стандартного ввода и вывода. Наверняка вы уже встречали в интернете вывод `Hello, World!` с использованием функции `printf()`, объявленной в `stdio.h`.

Как же это сделать? Сделаем это с помощью системного вызова `write`, к которому программа на Си обращается с помощью функции `write(int fd, char *buf, size_t nbytes)`.

Аргумент | Описание
--- | ---
fd | файловый дескриптор, может принимать значения 0, 1, 2 - стандартный ввод, стандартный вывод и стандартная ошибка соответсвенно
buf | указывается массив символов вашей программы, куда посылаются или откуда берутся данные
nbytes | количство пересылаемых байтов (размер buf должен быть равен nbytes)

Вывод на экран одного символа выглядит так:
```C
#include <unistd.h>	\\подключаем заголовочный файл

int	main(void)	\\объявляем функцию main, которая является точкой входа в программу, без неё программа не будет работать
{
	write(1, "H", 1);	\\Используем функцию системного вывода для вывода в консоль символьной строки "H" размером в 2 бита
	return (0);
}
```
> Обратите внимание, код написан соглачно требованиям Школы 21, norminette не выдаёт ошибок.
Размер символа в Си равен 1 бит. Почему тогда в комментарии рамер указан 2 бита, а в функции третим аргументом взят 1 бит? Потому что символьная строка является массивом символов, в котором последним элементом является специальный символ конца строки `'\0'` - нуль-терминатор и он тоже имеет размер 1 бит. Следовательно, размер `"H"` равен 2 бит - строка заключается в двойные ковычки `""`.Символ заключается в одинарные ковычки `''`, размер символа `'H'` равен 1 бит. Когда мы записываем внутри `""` определённое количесвто символов, мы чётко видим, где заканичивается строка и на каком символе. Но компьютер этого не видит и потому компилятор вконце такой строки автоматически вставляет нуль-терминатор, и он скрыт от глаз программиста. На экран мы хотим вывести только букву `H`, потому достатоно передать только 1 бит. Массив символов отличается от строки символов тем, что в последнем его элементе нет нуль-терминатора и он не является строкой. Надеюсь, понятно объяснил?)

Результат выполнения кода выглядит так:

![write_1](https://i.ibb.co/9vKkdMK/write-1.png)

Теперь логич будет посчитать количество символов в строке `"Hello, World!\n"`, учесть при этом символ переноса каретки `'\n'`, получится 15, следовательно 15 бит. Укажем это в нашем коде:

```C
#include <unistd.h>

int main(void)
{
	write(1, "Hellow, World!\n", 15);

	return (0);
}
```
Результат:

![write_2](https://i.ibb.co/wQmB7y4/write-2.png)

В первом примере выше я не показал, как запускать проверу norminette и компилировать код, но это можно увидеть в этом примере. Видно, что код написан по стандарту, и в результате его выполнения получаем в выводе `Hello, World!`. Да, теперь мой терминал выглядит так. Если будет интересно узнать, как я сменил стиль bash-оболочки, могу позже об этом написать статью.

[Оглавление](#content)

---
