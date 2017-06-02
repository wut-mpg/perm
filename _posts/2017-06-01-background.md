---
layout: task
title: Wykrywanie ruchomych obiektów
category: lab
lab: 6
task: 1
brief: Analiza sekwencji obrazów, estymacja parametrów tła oraz segmentacja obiektów ruchomych
---

## Przykładowe obrazy wynikowe

### Obraz wejściowy

![]({{ site.baseurl }}/public/l6/1.png)

### Maska wygenerowana przez algorytm estymacji parametrów tła

Tutaj użyty algorytm MOG

![]({{ site.baseurl }}/public/l6/2.png)

### Maska po operacjach morfologicznych

Połaczenie bliskich fragmentów maski w większą całość.

![]({{ site.baseurl }}/public/l6/3.png)

### Wykryte kontury

Segmenty o rozmiarze poniżej ustalonego progu są odrzucane (np. fragmenty głowy).

![]({{ site.baseurl }}/public/l6/4.png)

### Oznaczone obiekty

![]({{ site.baseurl }}/public/l6/5.png)
