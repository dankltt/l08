---
# Front matter
title: "Лабораторная работа №8."
subtitle: "Элементы криптографии. Шифрование (кодирование) различных исходных текстов одним ключом"
author: "Силкина Мария Александровна"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
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

Освоить на практике применение режима однократного гаммирования на примере кодирования нескольких различных текстов одним ключом. 

# Задачи

1. Написать программу, которая должна определять вид шифротекстов при известных открытых текстах и при известном ключе. Также эта программа должна определить вид одного из текстов, зная вид другого открытого текста и  зашифрованный вид обоих текстов без использования ключа.

2. Ответить на контрольные вопросы

# Выполнение лабораторной работы 

##Теоретическая справка

Гаммирование представляет собой наложение (снятие) на открытые (зашифрованные) данные последовательности элементов других данных, полученной с помощью некоторого криптографического алгоритма, для получения зашифрованных (открытых) данных. Иными словами, наложение гаммы — это сложение её элементов с элементами открытого (закрытого) текста по некоторому фиксированному модулю, значение которого представляет собой известную часть алгоритма шифрования

## Выполнение задач 

Первым шагом написала функцию шифрования, которая определяет вид шифротекстов при известном ключе и известном открытом тексте. В выводе я получила наши изначальные тексты, их представление в шестнадцатеричной системе, рандомный ключ и зашифрованные тексты. (рис - @fig:001)

![Функция, шифрующая данные и ее выполнение](image/1.png){ #fig:001 width=70% }

Далее я создала функцию для дешифрования, которая при знании зашифрованных текстов и иодного изначального, может найти второй (неизвестный) текст. (рис - @fig:002)

![Функция, дешифрующая данные и ее выполнение](image/2.png){ #fig:002 width=70% }

##Контрольные вопросы

1. Зная один из текстов, мы можем определить другой, вопспользовавшись следующей формулой: $C_1 \oplus C_2 \oplus + P_1 = P_1 \oplus P_2 \oplus + P_1 = P_2$, где $C_1$ и $C_2$ - шифротексты. Т.е. ключ в данной формуле не используется.

2. При повторном использовании ключа при шифровании текста получим исходное сообщение.  

3. Режим шифрования однократного гаммирования одним ключом двух открытых текстов реализуется по следующей формуле:
$$C_1 = P_1 \oplus + K$$
$$C_2 = P_2 \oplus + K,$$

где $C_i$ - шифротексты, $P_i$ - открытые тексты, $K$ - единый ключ шифровки  

4. Недостатки шифрования одним ключом двух открытых текстов:  
- Имея на руках одно из сообщений в открытом виде и оба шифротекста, злоумышленник способен расшифровать каждое сообщение, не зная ключа.  
- Зная шаблон сообщений, злоумышленник получает возможность определить те символы сообщения $P_2$, которые находятся на позициях известного шаблона сообщения $P_1$.

5. Преимущество шифрования одним ключом двух текстов заключается в том, что такой подход помогает упростить процесс шифрования и дешифровки. Также, при отправке сообщений между двумя компьютерами, удобнее пользоваться одним общим ключом для передаваемых данных

# Выводы

Освоила использования однократного гаммирования для шифрования и дешифрования данных.

# Библиография

1. Кулябов Д. С., Королькова А. В., Геворкян М. Н. Информационная безопасность компьютерных сетей. Лабораторная работа № 8. Элементы криптографии. Шифрование (кодирование) различных исходных текстов одним ключом.