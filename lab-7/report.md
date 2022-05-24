---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №7"
subtitle: "Модель распространения рекламы - вариант 48"
author: "Казаков Александр НПИбд-02-19"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
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
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the υalue makes tex try to haυe fewer lines in the paragraph.
  - \interlinepenalty=0 # υalue of the penalty (node) added after each line of a paragraph.
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
  - \usepackage{amsmath}
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучить модель эффективности рекламной кампании

# Задание

1.	Изучить модель эффективности рекламной кампании.
2.	Построить графики распространения рекламы по заданным математическим моделям.
3.	Определить для случая 2 момент времени, в который скорость распространения рекламы будет максимальной.

# Выполнение лабораторной работы

## Теоретические сведения

Организуется рекламная кампания нового товара или услуги. Необходимо, чтобы прибыль будущих продаж с избытком покрывала издержки на рекламу. Вначале расходы могут превышать прибыль, поскольку лишь малая часть потенциальных покупателей будет информирована о новинке. Затем, при увеличении числа продаж, возрастает и прибыль, и, наконец, наступит момент, когда рынок насытиться, и рекламировать товар станет бесполезным.

Предположим, что торговыми учреждениями реализуется некоторая продукция, о которой в момент времени $t$ из числа потенциальных покупателей $N$ знает лишь $n$ покупателей. Для ускорения сбыта продукции запускается реклама по радио, телевидению и других средств массовой информации. После запуска рекламной кампании информация о продукции начнет распространяться среди потенциальных покупателей путем общения друг с другом. Таким образом, после запуска рекламных объявлений скорость изменения числа знающих о продукции людей пропорциональна как числу знающих о товаре покупателей, так и числу покупателей о нем не знающих

Модель рекламной кампании описывается следующими величинами.
Считаем, что $\frac{dn}{dt}$ - скорость изменения со временем числа потребителей, узнавших о товаре и готовых его купить,
$t$ - время, прошедшее с начала рекламной кампании,
$N$ - общее число потенциальных платежеспособных покупателей,
$n(t)$ - число  уже информированных клиентов.
Эта величина пропорциональна числу покупателей, еще не знающих о нем, это описывается следующим образом
$\alpha _1(t)(N-n(t))$, где $\alpha _1>0$ -  характеризует интенсивность рекламной кампании (зависит от затрат на рекламу в данный момент времени).
Помимо этого, узнавшие о товаре потребители также распространяют полученную информацию среди потенциальных покупателей, не знающих о нем (в этом случае работает т.н. сарафанное радио). Этот вклад в рекламу описывается величиной  $\alpha _2(t)n(t)(N-n(t))$. эта величина увеличивается с увеличением потребителей узнавших о товаре.

Математическая модель распространения рекламы описывается уравнением:

$$\frac{dn}{dt} = (\alpha _1(t) + \alpha _2(t)n(t))(N-n(t))$$

При $\alpha _1(t) >> \alpha _2(t)$ получается модель типа модели Мальтуса, решение которой имеет вид 

![График решения уравнения модели Мальтуса](image/01.png){ #fig:001 width=70% height=70% }

В обратном случае $\alpha _1(t) << \alpha _2(t)$ получаем уравнение логистической кривой

![График логистической кривой](image/02.png){ #fig:002 width=70% height=70% }



## Задача

Постройте график распространения рекламы, математическая модель которой описывается следующим уравнением:

1.	$\frac{dn}{dt} = (0.766 + 0.000082n(t))(N-n(t))$
2.	$\frac{dn}{dt} = (0.0000866 + 0.7n(t))(N-n(t))$
3.	$\frac{dn}{dt} = (0.95\sin(t) + 0.32\cos(9t)n(t))(N-n(t))$

При этом объем аудитории $N$ = 1930, в начальный момент о товаре знает 27 человек.

Для случая 2 определите в какой момент времени скорость распространения рекламы будет иметь максимальное значение.

```
model lab7_1

parameter Real a = 0.766;
parameter Real b = 0.000082;
parameter Real N = 1930;

Real n(start = 27);

equation
der(n) = (a + b * n) * (N - n);

annotation(experiment(StartTime = 0, StopTime = 10, Interval = 0.05));
end lab7_1;

```

![График распространения рекламы для случая 1](image/03.png){ #fig:003 width=70% height=70% }

```
model lab7_2

parameter Real a = 0.0000866;
parameter Real b = 0.7;
parameter Real N = 1930;

Real n(start = 27);

equation
der(n) = (a + b * n) * (N - n);

annotation(experiment(StartTime = 0, StopTime = 0.1, Interval = 0.05));
end lab7_2;

```

![График распространения рекламы для случая 2](image/04.png){ #fig:004 width=70% height=70% }

Vаксимальная скорость распространения рекламы достигается при $t=0$

```
model lab7_3

parameter Real a = 0.95;
parameter Real b = 0.95;
parameter Real N = 1930;

Real n(start = 27);

equation
der(n) = (a * sin (1 * time) + b * cos (9 * time) * n) * (N - n); 

annotation(experiment(StartTime = 0, StopTime = 0.1, Interval = 0.05));
end lab7_3;

```

![График распространения рекламы для случая 3](image/05.png){ #fig:005 width=70% height=70% }

# Выводы

Изучена модель эффективности рекламы, построены графики распространения рекламы.

# Список литературы {.unnumbered}

1. [Документация по системе Modelica – Режим доступа: https://www.modelica.org/](https://www.modelica.org/)
2. [Введение в математическое моделирование : учебное пособие / В.Н. Ашихмин, М.Б. Гитман, И.Э. Келлер [и др.]; Под ред. П.В. Трусова. - Электронные текстовые данные. - М. : Логос, 2015. - 440 с. : ил. - (Новая Университетская Библиотека). - ISBN 978-5-98704-637-1.](http://lib.rudn.ru/ProtectedView/Book/ViewBook/5847)