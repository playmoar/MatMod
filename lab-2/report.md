---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе №2"
subtitle: "Задача о погоне - вариант 48"
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
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Изучение примера построения математических моделей для выбора правильной стратегии при решении задач поиска. 

# Задание

1. Провести необходимые рассуждения и вывод дифференциальных уравнений, если скорость катера больше скорости лодки в n раз.
2. Построить траекторию движения катера и лодки для двух случаев. 
3. Определить по графику точку пересечения катера и лодки.

# Выполнение лабораторной работы

## Условие задачи

На море в тумане катер береговой охраны преследует лодку браконьеров.
Через определенный промежуток времени туман рассеивается, и лодка обнаруживается на расстоянии 16.7 км от катера. 
Затем лодка снова скрывается в тумане и уходит прямолинейно в неизвестном направлении. 
Известно, что скорость катера в 4.5 раза больше скорости браконьерской лодки

## Вывод дифференциальных уравнений

$t_0=0, X_0=0$  - местонахождение лодки браконьеров в момент обнаружения
$X_0=16,7$   - место нахождения катера береговой охраны относительно лодки браконьеров в момент обнаружения лодки.

Вводим полярные координаты. Будем считать, что полюс - это точка обнаружения браконьеров $x_0=\theta=0$
Полярная ось r будет проходить через точку местонахождения лодки береговой охраны.

Траектория движения катера должна быть такой, чтобы и катер и лодка находились на одном расстоянии от полюса $\theta$ . Поэтому, сначала катеру береговой охраны придётся двигаться прямолинейно. Когда он окажется на том же расстоянии от места обнаружения, что и лодка браконьеров, катер начнёт двигаться вокруг полюса. 

За время $t$ лодка пройдет $x$, а катер $x-k$ (или $x+k$, в зависимости от случая).
Так как время, которое они двигались, одинаково, можем составить следующее уравнение:
$\frac{x}{v} = \frac{x+k}{v}$ для первого случая, 
$\frac{x}{v} =  \frac{x-k}{v}$ для второго случая.

Отсюда находим $x_1$ и $x_2$

$x_1=\frac{167}{55}$ ,при $\theta=0$

$x_2=\frac{167}{35}$ ,при $\theta=-\pi$

Далее рассмотрим скорость катера. Она складывается из скорости радиальной и тангенциальной. Таким образом
$v_r=r\frac{d\theta}{dt}=v$

$v_t=r\frac{d\theta}{dt}$.
По теореме Пифагора тангенциальная скорость также равна $v_t= \sqrt{20,25v_r^2-v^2}$. 
Поскольку, радиальная скорость равна $v$,  $v_t= \sqrt{20,25v^2-v^2 }$. Следовательно, $v_t=v\frac{\sqrt{77}}{2}$.

Получим $r\frac{d\theta}{dt}=v\frac{\sqrt{77}}{2}$

Решение исходной задачи сводится к решению системы из двух дифференциальных уравнений 

$$
 \begin{cases}
   \frac{dr}{dt}=v
	\\   
	r\frac{d\theta}{dt}=v\frac{\sqrt{77}}{2}
 \end{cases}
$$

с начальными условиями

$$
 \begin{cases}
   \theta_0=0
   \\
	r_0=\frac{167}{55}
 \end{cases}
\
$$

$$
 \begin{cases}
   \theta_0=-\pi
   \\
	r_0=\frac{167}{35}
 \end{cases}
\
$$

Из полученной системы возможно исключить производную по t
Получим следующее уравнение: $\frac{dr}{d\theta}=\frac{2r}{\sqrt{77}}$
 
## Код программы

```
from math import *
import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plot

k=16.7 
fi = pi*3/4 

def f1(tetha, r): 
    dr=2*r/sqrt(77)
    return dr

def f2(t): 
    xt = tan(fi)*t
    return xt

r01=167/55
r02=167/35

tetha1 = np.arange(0, 2*pi, 0.01)
r1_1 = odeint(f1, r01, tetha1)
r1_2 = odeint(f1, r02, tetha1)

t=np.arange(0, 10, 1)
tetha2=np.arctan(f2(t)/t)
r2 = np.sqrt(t * t+ f2(t) * f2(t))

plot.polar(tetha1, r1_1, 'red', label = 'катер')
plot.polar(tetha2, r2, 'green', label = 'лодка')

plot.legend()

plot.polar(tetha1, r1_2, 'blue', label = 'Катер')
plot.polar(tetha2, r2, 'goldenrod', label = 'Лодка')

plot.legend()
```


## Полученные в результате моделирования траектории

![Траектории движения для первого случая](image/01.png){ #fig:001 width=70% height=70% }

![траектории движения для второго случая](image/02.png){ #fig:002 width=70% height=70% }

# Вывод

Рассмотрена задача о погоне. Выведены соответствующие дифференциальные уравнения. Построена математическая модель для выбора правильной стратегии.

# Список литературы {.unnumbered}

1. [Введение в математическое моделирование : учебное пособие / В.Н. Ашихмин, М.Б. Гитман, И.Э. Келлер [и др.]; Под ред. П.В. Трусова. - Электронные текстовые данные. - М. : Логос, 2015. - 440 с. : ил. - (Новая Университетская Библиотека). - ISBN 978-5-98704-637-1.](http://lib.rudn.ru/ProtectedView/Book/ViewBook/5847)