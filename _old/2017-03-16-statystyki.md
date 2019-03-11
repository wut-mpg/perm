---
layout: task
title: Statystyki sygnałów
category: lab
lab: 2
task: 2
brief: Generowanie sygnałów losowych oraz obliczanie ich statystyk.
---

## Generowanie sygnałów losowych

Proszę wygenerować dwa sygnały losowe (długości 512 próbek) o rozkładzie normalnym (używając funkcji [random](http://www.mathworks.com/help/stats/random.html)), mające następujące parametry:

   * **N1** o średniej = 0 oraz odchyleniu standardowym = 1 
   * **N2** o średniej = 2 oraz odchyleniu standardowym = 2 

oraz sygnał losowy **U** o rozkładzie jednostajnym z przedziału [1, 3].

Dla wygenerowanych sygnałów proszę obliczyć średnią oraz odchylenie standardowe. **Dlaczego różnią się one od wartości użytych do generacji danych?**

Proszę wyświetlić wszystkie sygnały na jednym wykresie.

![]({{ site.baseurl }}/public/l2/2_1A.png)
![]({{ site.baseurl }}/public/l2/2_1B.png)

## Statystyki ruchome

Dla sygnałów wygenerowanych w poprzednim zadaniu proszę wyznaczyć statystyki ruchome (kroczące) - średnią oraz odchylenie standardowe. Wyniki zilustrować na wykresach oraz skomentować.

![]({{ site.baseurl }}/public/l2/2_2.png)

## Histogramy rozkładu

Dla sygnałów **N1**, **N2** oraz **U** wyznaczyć histogramy wartości dla 10 oraz 90 przedziałów wartości (używając funkcji [linspace](http://www.mathworks.com/help/matlab/ref/linspace.html) oraz [hist](http://www.mathworks.com/help/matlab/ref/hist.html)). Proszę wyświetlić wykresy histogramów (używając funkcji [bar](http://www.mathworks.com/help/matlab/ref/bar.html)).
**Czy kształty rozkładów są zgodne z oczekiwanymi?**

![]({{ site.baseurl }}/public/l2/2_3.png)
