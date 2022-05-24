---
# Front matter
title: "Отчёт по лабораторной работе №1"
subtitle: "Система контроля версий Git"
author: "Казаков Александр НПИбд-02-19"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
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
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучить работу с системой контроля версий git.

# Выполнение лабораторной работы

Созданы учетная запись и репозиторий на github.com 

![Создание репозитория](image/01.png){ #fig:001 width=70% height=70% }

Инициализирован локальный репозиторий, создан файл README.md, установлены имя пользователя и e-mail, сделан первый commit.

![Инициализация репозитория, README, commit](image/02.png){ #fig:002 width=70% height=70% }

Создан SSH-ключ, созданный ключ добавлен в настройках пользователя github.com.

![Создание SSH-ключа на устройстве](image/03.png){ #fig:003 width=70% height=70% }

Загружены файлы лицензионного соглашения и gitignore. Получен доступ к сетевому репозиторию, загруженные файлы отправлены в репозиторий.

![Загрузка файлов](image/04.png){ #fig:004 width=70% height=70% }

Создана тестовая ветка, начат и завершён тестовый релиз.

![Инициализация git-flow, тестовый релиз](image/05.png){ #fig:005 width=70% height=70% }

Внесённые изменения отправлены в репозиторй.

![Отправка изменений в репозиторий](image/06.png){ #fig:006 width=70% height=70% }


# Вывод

Изучена работа с системой контроля версий git, приобретены навыки создания и управления репозиторием, ветками и релизами.

# Список литературы {.unnumbered}

1. [Документация по системе git – Режим доступа: https://git-scm.com/book/ru/v2](https://git-scm.com/book/ru/v2)
