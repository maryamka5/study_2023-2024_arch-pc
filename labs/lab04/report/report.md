---
## Front matter
title: "Отчёт по лабораторной работе 4"
subtitle: "Архитектура компьютеров"
author: "Ел Вакил Марьям Махмоудовна НБИбд-03-23"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью работы является освоение процедуры компиляции и сборки программ, написанных на ассемблере NASM.

# Задания

1. Изучить пример прораммы Hello world

2. Опробовать и освоить процесс компиляции программы

3. Внести изменения в программу

# Выполнение лабораторной работы

## Программа Hello world

Я создала каталог lab04, используя команду mkdir, затем перешла в него с помощью команды cd. Внутри этого каталога я создала файл hello.asm.

![Создание файла](image/01.png){ #fig:001 width=70%, height=70% }

Далее, я открыла файл в редакторе и написала код программы в соответствии с заданием.

![Код программы](image/02.png){ #fig:002 width=70%, height=70% }

## Транслятор NASM

Затем я транслировала файл с помощью команды nasm, указав опцию -f. 
Ключ -f указывает транслятору, что нужно создать бинарные файлы в формате ELF.

Если текст программы был набран без ошибок, то транслятор преобразует текст программы 
из файла hello.asm в объектный код, который будет записан в файл hello.o. 
Таким образом, имена всех файлов формируются из имени входного файла и расширения по умолчанию.
В случае возникновения ошибок, объектный файл не будет создан, а при запуске транслятора 
появятся сообщения об ошибках или предупреждениях.

В результате, я получила объектный файл hello.o.

Полный вариант командной строки nasm выглядит следующим образом:

```nasm [-@ косвенный_файл_настроек] [-o объектный_файл] [-f формат_объектного_файла] [-l листинг] [параметры...] [--] исходный_файл```

Затем транслировала файл с помощью команды nasm и дополнительными опциями: -o, -g, -l. 
Опция -o позволяет задать имя объектного файла. 
Опция -g добавляет отладочную информацию. 
Опция -l создает файл листинга.

В итоге, я получила файл листинга list.lst, объектный файл obj.o, 
и в программу была добавлена отладочная информация.

![Трансляция программы](image/03.png){ #fig:003 width=70%, height=70% }

## Компоновщик LD

Выполнила компоновку командой ld и получила исполняемый файл.

Еще раз выполнила компоновку для объектного файла obj.o и получила исполняемый файл main.

Затем я запустила исполняемые файлы.

![Компоновка программы и звпуск](image/04.png){ #fig:004 width=70%, height=70% }

## Самостоятельная работа 

Скопировала программу в файл lab4.asm.

![Копирование программы](image/05.png){ #fig:005 width=70%, height=70% }

Изменила сообщение Hello world на свое имя.

![Код программы](image/05.png){ #fig:005 width=70%, height=70% }

Оттранслировала полученный текст программы lab4.asm в объектный файл. Выполнила
компоновку объектного файла и запустила получившийся исполняемый файл.

![Проверка программы lab4.asm](image/06.png){ #fig:006 width=70%, height=70% }

# Выводы

Освоили процесс компиляции и сборки программ, написанных на ассемблере nasm.
