---
## Front matter
lang: ru-RU
title: Знакомство с системой контроля версий git
author: |
	Казаков Александр НПИбд-02-19\inst{1}

institute: |
	\inst{1}Российский Университет Дружбы Народов

date: 23 мая, 2022, Москва, Россия

## Formatting
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true

---

# Цели и задачи работы

## Цель лабораторной работы

Изучить работу с системой контроля версий git.

## Задачи лабораторной работы

1. Создать учетную запись на github.com

2. Создать и настроить репозиторий

3. Изучить механизм управления версиями, ветками.

# Процесс выполнения лабораторной работы

## Создание учетной записи и репозитория на github.com 

![Создание репозитория](image/01.png){ #fig:001 width=70% height=70% }

## Инициализация локального репозитория

Создан файл README.md, установлены имя пользователя и e-mail, сделан первый commit.

![Инициализация репозитория, README, commit](image/02.png){ #fig:002 width=70% height=70% }

## Создание SSH-ключа
Создан SSH-ключ. Созданный ключ добавлен в настройках пользователя github.com.

![Создание SSH-ключа на устройстве](image/03.png){ #fig:003 width=70% height=70% }

## Отправка файлов в репозиторий
Загружены файлы лицензионного соглашения и gitignore. Получен доступ к сетевому репозиторию, загруженные файлы отправлены в репозиторий.

![Загрузка файлов](image/04.png){ #fig:004 width=70% height=70% }

## Управление ветками и версиями 
Создана тестовая ветка, начат и завершён тестовый релиз.

![Инициализация git-flow, тестовый релиз](image/05.png){ #fig:005 width=70% height=70% }

## Отправка внесённых изменений в репозиторий

![Отправка изменений в репозиторий](image/06.png){ #fig:006 width=70% height=70% }

# Итоги

## Вывод

Изучена работа с системой контроля версий git, приобретены навыки создания и управления репозиторием, ветками и релизами.