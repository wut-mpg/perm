---
layout: task
title: Operacje punktowe
category: lab
lab: 3
task: 1
brief: Przegląd podstawowych operacji punktowych - analiza histogramu, progowanie, przestrzenie barw.
---

## Informacje wstępne

Operacje punktowe na obrazie działają całkowicie bezkontekstowo - wartość 
danego punktu (barwa, jasność bądź inny parametr) 
jest zmieniana jedynie w zależności od niej samej:

$$
Out(i,j) = f\big(In(i,j)\big)
$$

Pierwszą grupą operacji tego typu są operacje liniowe, np. zmiana jasności czy kontrastu:

$$
Out(i,j) = C \cdot In(i,j) + B
$$

Ogólniejszą grupą są przekształcenia nieliniowe LUT, gdzie wartość wyjściowa 
jest odczytywana z tablicy (<b>l</b>ook<b>u</b>p <b>t</b>able). 

![]({{site.baseurl}}/public/l3/lut.png)

Szczególnym przypadkiem przekształcenia nieliniowego jest progowanie obrazu. 
Jego celem jest wyodrębnienie w obrazie obszarów zainteresowania, 
a więc punktów, które spełniają pewne kryteria, w celu ich dalszej analizy 
(wyodrębnienie obiektu zainteresowania od tła).

![]({{site.baseurl}}/public/l3/thr.png)

Podczas przetwarzania wstępnego obrazu przydaje się analiza jego histogramu,
czyli rozkładu wartości jednego bądź wielu parametrów punktu (np. jasności).
Histogram pozwala szybko określić, czy obraz jest prawidłowo naświetlony,
a także określić miejsce progowania w przypadku obrazów bimodalnych.


Do operacji punktowych (bezkontekstowych) zalicza się też konwersje pomiędzy
przestrzeniami barw. W przetwarzaniu obrazów często spotyka się przestrzenie
RGB (jest to powszechny sposób zapisu i interpretacji obrazów cyfrowych), 
HSV/HSL (podział na barwę, jasność i nasycenie), YCbCr/YUV (luminancja i chrominancja),
Lab (percepcyjna odległość między kolorami).
Wybór właściwej przestrzeni zależy od zastosowania, zwykle jednak wygodniej
jest korzystać z przestrzeni, które niezależnie kodują informację o barwie
i jasności (np. HSV), niż z przestrzeni mieszanych (RGB).

![]({{site.baseurl}}/public/l3/colors.png)

## Rozciąganie i wyrównanie histogramu

Proszę uruchomić zadanie `EqualizeHistogram.xml`

### Struktura zadania

   * **Sequence** - odczytywanie obrazów z dysku
   * **B/C** - zmiana kontrastu i jasności obrazu z możliwością wyrównania histogramu
   * **Histogram** - obliczanie i wyświetlanie histogramu obrazu
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę spróbować rozciągnąć histogram obrazu wejściowego za pomocą modyfikacji jasności i kontrastu
2. Porównać wyniki uzyskane przy rozciąganiu histogramu z wynikiem wyrównania histogramu (`equalize_histogram`)

## Przestrzenie barw i progowanie

Proszę uruchomić zadanie `ColorSpaces.xml`

### Struktura zadania

   * **Source** - odczytywanie obrazów z sensora
   * **Color** - konwersja z przestrzeni RGB do HSV
   * **RGBLUT** - Progowanie obrazu w przestrzeni RGB
   * **HSVLUT** - Progowanie obrazu w przestrzeni HSV
   * **Window** - wyświetlanie obrazów
   
### Do zrobienia

1. Proszę wybrać sobie obiekt o w miarę jednolitej barwie
2. Dla wybranego przedmiotu proszę ustalić parametry progowania w przestrzeniach 
   RGB oraz HSV tak, aby możliwie dobrze wydzielić obiekt z tła

## Progowanie automatyczne

Proszę uruchomić zadanie `Otsu.xml`

### Struktura zadania

   * **Sequence** - odczytywanie obrazów z dysku
   * **Histogram** - obliczanie i wyświetlanie histogramu obrazu
   * **Threshold** - progowanie obrazu
      * `thresh` - poziom progowania
      * `Otsu` - automatyczne wyznaczenie poziomu progowania
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę dobrać ręcznie próg dla obrazów testowych oraz porównać go z wartością dobraną przez algorytm Otsu.
   Oczekiwanym efektem działania jest wydzielenie tekstu od tła.
