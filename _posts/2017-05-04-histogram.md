---
layout: task
title: Rozpoznawanie obiektów oparte o histogram
category: lab
lab: 4
task: 1
brief: Identyfikacja wskazanego obiektu poprzez analizę histogramu barwnego (barwa-nasycenie).
---

## Informacje wstępne

Oprócz histogramów jasności (takich, jak omawiane na poprzednich zajęciach)
z obrazu kolorowego można wyznaczyć także bardziej złożone histogramy wielowymiarowe.
Jeżeli na wejściu dostajemy obraz w przestrzeni HSV, zamiast analizy jasności
(która znacząco zależy od oświetlenia) można wyznaczyć rozkład wartości
barwy w zależności od nasycenia.
Przy podziale każdej ze składowych na pewną ilość kubełków, w każdym z nich zliczane
są te punkty obrazu, których kombinacja barwy i nasycenia wpada do odpowiedniego przedziału.

![]({{ site.baseurl }}/public/l4/hs.png)

Taki histogram, wyznaczony dla jakiegoś obiektu, może być traktowany jako jego
kompaktowa reprezentacja. Porównując następnie tego typu zapamiętane rozkłady
z histogramem obrazu (bądź jego fragmentu) pozyskanego z kamery można w łatwy 
sposób stwierdzić, czy jest szansa na rozpoznanie interesującego obiektu czy nie.

## Struktura zadania

Proszę uruchomić zadanie `Hist2D.xml`

   * **Source** - pozyskiwanie obrazów z sensora
   * **Mask** - określenie obszaru zainteresowania
   * **Hist** - wyznaczenie dwuwymiarowego histogramu H-S (barwa-nasycenie) 
                dla wybranego obszaru zainteresowania oraz obliczenie obrazu
                po projekcji wstecznej
   * **Detector** - detekcja obiektów na podstawie histogramu
      * `updateObject` - nauczenie/aktualizacja histogramu dla obiektu `object_name`
   * **Window** - wyświetlanie obrazów
      * `In` - obraz wejściowy z zaznaczonym obszarem zainteresowania i naniesionymi
               wynikami procesu rozpoznawania
      * `Hist` - histogram dla obszaru zainteresowania
      * `Back` - obraz po wstecznej projekcji histogramu

## Do zrobienia

1. Proszę wybrać co najmniej 3 obiekty (bądź klasy obiektów) i zapamiętać
   je w komponencie **Detector**
2. Proszę zweryfikować poprawne rozpoznawanie wybranych obiektów przy innych
   punktach widzenia bądź innych reprezentantach danej klasy
3. Proszę spróbować znaleźć przykłady negatywne, czyli należące do innej klasy
   niż nauczone, natomiast dające wysokie wyniki rozpoznawania



