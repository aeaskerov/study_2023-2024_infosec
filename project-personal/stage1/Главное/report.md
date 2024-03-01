---
## Front matter
title: "Индивидуальный проект. Этап 1."
subtitle: "Установка Kali Linux"
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

Установить и настроить Kali Linux.

# Выполнение лабораторной работы

Создадим новую виртуальную машину, нажав кнопку Создать.

![Создание новой ВМ](image/1.png){#fig:001 width=70%}

Укажем имя ВМ, выберем образ для неё.

![Указание имени ВМ](image/2.png){#fig:002 width=70%}

Выделим основную память и число процессоров.

![Настройка основной памяти и числа процессоров](image/3.png){#fig:003 width=70%}

Определим размер виртуального жёсткого диска.

![Указание размера виртуального жёсткого диска](image/4.png){#fig:004 width=70%}

Увидим итоговые настройки ВМ.

![Итоговые настройки ВМ](image/5.png){#fig:005 width=70%}

Запустим ВМ и укажем язык системы.

![Выбор языка системы](image/6.png){#fig:006 width=70%}

Укажем страну.

![Указание страны](image/7.png){#fig:007 width=70%}

Укажем раскладку клавиатуры.

![Выбор раскладки клавиатуры](image/8.png){#fig:008 width=70%}

Подождём пока пройдёт загрузка.

Укажем имя хоста.

![Указание имени хоста](image/9.png){#fig:009 width=70%}

Укажем пароль.

![Указание пароля](image/10.png){#fig:010 width=70%}

Разделим диск.

![Разделение диска](image/11.png){#fig:011 width=70%}

Завершим разделение.

![Итог разделения диска](image/12.png){#fig:012 width=70%}

Выберем запись изменений на диск.

![Запись изменений на диск](image/13.png){#fig:013 width=70%}

Выберем ПО для установки.

![Выбор ПО для установки](image/14.png){#fig:014 width=70%}

Установим загрузчик GRUB.

![Установка загрузчика GRUB](image/15.png){#fig:015 width=70%}

Выберем устройство для загрузчика.

![Выбор устройства для загрузчика GRUB](image/16.png){#fig:016 width=70%}

Завершим установку и перезагрузим ВМ.

![Завершение установки](image/17.png){#fig:017 width=70%}

Авторизуемся.

![Рабочий стол в Kali Linux](image/18.png){#fig:018 width=70%}

# Выводы

Установлена и настроена Kali Linux.

# Список литературы{.unnumbered}

Kali Linux: Тестирование на проникновение и безопасность - Ш. Парасрам, А. Замм, Т. Хериянто и др. Питер, 2022. - 448с.
