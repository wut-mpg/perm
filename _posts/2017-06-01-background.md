---
layout: task
title: Usuwanie tła
category: lab
lab: 6
task: 1
brief: Analiza sekwencji obrazów, estymacja parametrów tła oraz segmentacja obiektów ruchomych
---

## Struktura zadania

Proszę uruchomić zadanie `BackgroundEstimation.xml`

   * **Source** - pozyskiwanie obrazów z sensora
   * **Sub** - usuwanie tła
      * `method` - wybrana metoda analizy tła (MOG, MOG2, CMG)
      * `rate` - współczynnik uczenia (0 - model tła nie jest uaktualniany, 
                 100 - model tła jest całkowicie zależny od ostatniego obrazu)
      * `automatic` - używaj automatycznie wyznaczonego współczynnika `rate`
      * `reset` - wyczyść model tła 
   * **Window** - wyświetlanie obrazu wejściowego oraz maski ruchu

## Do zrobienia

1. Po uruchomieniu zadania proszę poruszać sensorem i sprawdzić jakość oraz
   niezawodność działania metody RanSaC dla różnych płaszczyzn
