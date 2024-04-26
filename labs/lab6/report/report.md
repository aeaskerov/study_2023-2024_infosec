---
## Front matter
title: "Лабораторная работа №6"
subtitle: "Мандатное разграничение прав в Linux"
author: "Аскеров Александр Эдуардович"

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
lot: false # List of tables
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

Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux.

Проверить работу SELinx на практике совместно с веб-сервером Apache.

# Выполнение лабораторной работы

Войдём в систему с полученными учётными данными и убедимся, что SELinux работает в режиме enforcing политики targeted с помощью команд getenforce и sestatus.

![Проверка SELinux](image/1.png){#fig:001 width=70%}

Обратимся с помощью браузера к веб-серверу, запущенному на компьютере, и убедимся, что последний работает.

![Проверка работы веб-сервера](image/2.png){#fig:002 width=70%}

Найдём веб-сервер Apache в списке процессов, определим его контекст безопасности.

![Контекст безопасности веб-сервера](image/3.png){#fig:003 width=70%}

Посмотрим текущее состояние переключателей SELinux для Apache.

![Переключатели SELinux](image/4.png){#fig:004 width=70%}

Посмотрим статистику по политике с помощью команды seinfo, также определим множество пользователей, ролей, типов.

![Статистика по политике](image/5.png){#fig:005 width=70%}

Определим тип файлов и поддиректорий, находящихся в директории /var/www.

![Тип файлов и поддиректорий](image/6.png){#fig:006 width=70%}

Определим тип файлов, находящихся в директории /var/www/html.

![Тип файлов](image/7.png){#fig:007 width=70%}

Определим круг пользователей, которым разрешено создание файлов в директории /var/www/html.

![Круг пользователей с разрешением](image/8.png){#fig:008 width=70%}

Создадим от имени суперпользователя html-файл /var/www/html/test.html следующего содержания.

![html-файл](image/9.png){#fig:009 width=70%}

Проверим контекст созданного файла. Запишем контекст, присваиваемый по умолчанию вновь созданным файлам в директории /var/www/html.

![Контекст файла](image/10.png){#fig:010 width=70%}

Обратимся к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html.

Изучим справку man httpd_selinux.

Изменим контекст файла /var/www/html/test.html с httpd_sys_content_t на любой другой, к которому процесс httpd не должен иметь доступа, например, на samba_share_t.

![Изменение контекста](image/11.png){#fig:011 width=70%}

![Проверка контекста](image/12.png){#fig:012 width=70%}

Попробуем ещё раз получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1/test.html. Получено сообщение об ошибке.

Проанализируем ситуацию. Просмотрим log-файлы веб-сервера Apache. Также просмотрим системный лог-файл.

![Системный лог-файл](image/13.png){#fig:013 width=70%}

Посмотрим файл /var/log/audit/audit.log.

![Файл audit.log](image/14.png){#fig:014 width=70%}

Попробуем запустить веб-сервер Apache на прослушивание ТСР-порта 81 (а не 80, как рекомендует IANA и прописано в /etc/services). Для этого в файле /etc/httpd/httpd.conf найдём строчку Listen 80 и заменим её на Listen 81.

![Изменение порта](image/15.png){#fig:015 width=70%}

Выполним перезапуск веб-сервера Apache. Произошёл сбой из-за изменения порта.

Проанализируем лог-файлы.

![Файл messages](image/16.png){#fig:016 width=70%}

Просмотрим файлы /var/log/http/error_log, /var/log/http/access_log и /var/log/audit/audit.log и выясним, в каких файлах появились записи.

![Файл access_log](image/17.png){#fig:017 width=70%}

![Файл audit.log](image/18.png){#fig:018 width=70%}

Выполним следующую команду.

![Управление портами](image/19.png){#fig:019 width=70%}

![Управление портами](image/20.png){#fig:020 width=70%}

Порт 81 появился в списке.

Попробуем запустить веб-сервер Apache ещё раз. Теперь он запустился.

Вернём контекст httpd_sys_cоntent__t к файлу /var/www/html/test.html.

![Возврат контекста](image/21.png){#fig:021 width=70%}

После этого попробуем получить доступ к файлу через веб-сервер, введя в браузере адрес http://127.0.0.1:81/test.html.

Мы видим содержимое файла – слово «test».

Исправим обратно конфигурационный файл apache, вернув Listen 80.

![Изменение порта](image/22.png){#fig:022 width=70%}

Удалим привязку http_port_t к 81-му порту.

![Удаление привязки](image/23.png){#fig:023 width=70%}

Удалим файл /var/www/html/test.html.

![Удаление файла](image/24.png){#fig:024 width=70%}

# Выводы

Развиты навыки администрирования ОС Linux. Получено первое практическое знакомство с технологией SELinux.

Проверена работа SELinx на практике совместно с веб-сервером Apache.

# Список литературы{.unnumbered}

::: {#refs}
:::
1. [Веб-сервер Apache](https://httpd.apache.org/)
