---
layout: task
title: Optical flow
category: lab
lab: 6
task: 2
brief: Wyznaczenie wektorów ruchu algorytmami rzadkiego oraz gęstego potoku optycznego.
---

## Struktura zadania

Proszę uruchomić zadanie `OptFlow.xml`

   * **Source** - pozyskiwanie obrazów z sensora
   * **OptFlowLK** - algorytm Lukas-Kanade
      * opis parametrów `tracker` zgodny z argumentami funkcji [calcOpticalFlowPyrLK](http://docs.opencv.org/2.4/modules/video/doc/motion_analysis_and_object_tracking.html#calcopticalflowpyrlk)
   * **OptFlowFB** - algortm Farneback 
   * **Window** - wyświetlanie obrazu wejściowego oraz maski ruchu

## Do zrobienia

1. Po uruchomieniu zadania proszę poruszać sensorem i sprawdzić jakość oraz
   niezawodność działania metody RanSaC dla różnych płaszczyzn
