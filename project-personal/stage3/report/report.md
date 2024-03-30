---
## Front matter
title: "Индивидуальный проект. Этап 3."
subtitle: "Использование Hydra"
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

Научиться использовать инструмент Hydra для нахождения паролей для авторизации.

# Выполнение лабораторной работы

Запустим DVWA.Перейдём в раздел DVWA Security и установим уровень защиты на “Low”.

![Изменение уровня защиты на “Low”](image/1.png){#fig:001 width=70%}

Создадим файл passwords.txt, в котором укажем пароли для подстановки.

![Создание passwords.txt](image/2.png){#fig:002 width=70%}

Запишем варианты паролей в нём.

![Пароли для перебора](image/3.png){#fig:003 width=70%}

Откроем код веб-страницы и посмотрим метод отправки формы.

![Метод отправки формы](image/4.png){#fig:004 width=70%}

Видим, что используется метод “GET”.

Теперь откроем Инспектор, перейдём в раздел Storage и скопируем значение PHPSESSID.

![Значение PHPSESSID](image/5.png){#fig:005 width=70%}

Перейдём в консоль и воспользуемся Hydra – вставим полученное значение PHPSESSID в один из аргументов команды.

![Использование Hydra](image/6.png){#fig:006 width=70%}

По выполнении команды мы видим подходящие значения для авторизации. Введём их и успешно авторизуемся.

![Успешная авторизация](image/7.png){#fig:007 width=70%}

# Выводы

Изучено использование инструмента Hydra для нахождения паролей для авторизации.

# Список литературы{.unnumbered}

::: {#refs}
:::
1. [Использование Hydra](https://timcore.ru/2021/04/12/2-ujazvimost-dvwa-brute-force-uroven-low/)
