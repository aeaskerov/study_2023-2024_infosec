---
## Front matter
title: "Индивидуальный проект. Этап 5."
subtitle: "Использование burp suite"
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

Получить представление о работе с burp suite.

# Выполнение лабораторной работы

Включим burp suite.

![Запуск burp suite](image/1.png){#fig:001 width=70%}

Ознакомимся со стартовым экраном проекта.

![Начало работы](image/2.png){#fig:002 width=70%}

Включим перехват (“Intercept is on”).

![Запуск перехвата](image/3.png){#fig:003 width=70%}

Откроем браузер и укажем следующие настройки соединения.

![Настройка соединения](image/4.png){#fig:004 width=70%}

После этого мы переключаемся на burp suite и видим информацию по подключению.

![Информация по подключению от burp suite](image/5.png){#fig:005 width=70%}

Запустим apache2 и mysql.

![Запуск apache2 и mysql](image/6.png){#fig:006 width=70%}

Зайдём в DVWA.

![DVWA](image/7.png){#fig:007 width=70%}

# Выводы

Получено представление о работе с burp suite.

# Список литературы{.unnumbered}

::: {#refs}
:::
1. [portswigger](https://portswigger.net/)
