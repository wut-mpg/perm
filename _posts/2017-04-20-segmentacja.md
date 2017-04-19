---
layout: task
title: Segmentacja
category: lab
lab: 3
task: 3
brief: Segmentacja obrazu. Wyznaczanie krawędzi i spójnych regionów. Deskryptory kształtu 2D.
---

## Informacje wstępne

Segmentacja obrazu ma na celu przekształcenie obrazu do postaci danych wyższego
poziomu, łatwiejszej do wykorzystania w dalszych obliczeniach. Podstawowe 
rodzaje segmentów to krawędzie oraz regiony. Istotny w segmentacji jest fakt
jawnego rozróżnienia pomiędzy różnymi obiektami (etykietowanie), w przeciwieństwie
do samego procesu detekcji krawędzi, gdzie wszystkie były oznaczane jedynie
białym kolorem w obrazie.

Na podstawie obrazu binarnego (takiego, jak uzyskanego po przekształceniu Canny'ego
bądź po progowaniu) można wyznaczyć łańcuchy spójnych punktów, tworzące pojedynczy kontur
([findContours](http://docs.opencv.org/2.4/doc/tutorials/imgproc/shapedescriptors/find_contours/find_contours.html)).
Jeżeli znane są dodatkowe ograniczenia na kształt poszukiwanego konturu,
możliwe jest wykorzystanie specjalizowanych wersji transformaty Hough'a
do detekcji linii ([HoughLines](http://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/hough_lines/hough_lines.html))
oraz okręgów ([HoughCircles](http://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/hough_circle/hough_circle.html)).

Przy analizie kształtów dwuwymiarowych wykorzystuje się ich kilka podstawowych własności.
Na podstawie powierzchni i obwodu można wyznaczyć współczynnik krągłości, który może być
wykorzystany jako podstawowy wyróżnik kształtów okrągłych od bardziej nieregularnych.
Istotną informację wnoszą też [momenty geometryczne](http://docs.opencv.org/2.4/modules/imgproc/doc/structural_analysis_and_shape_descriptors.html),
pozwalające na badanie od najprostszych cech kształtu (jak jego środek masy)
po skomplikowane struktury geometryczne.

## Transformata Hough'a

Proszę uruchomić zadanie `HoughCircles.xml`

### Struktura zadania

   * **Sequence** - odczytywanie obrazów z dysku
   * **Hough** - detekcja okręgów za pomocą transformaty Hough'a; istotne parametry:
      * `minDist` - minimalna odległość pomiędzy okręgami
      * `[min/max]CircleRadius` - ograniczenia rozmiaru okręgów
      * `cannyHigherThreshold` - górny próg w detektorze Canny'ego
      * `accumulatorThreshold` - minimalna wartość funkcji odpowiedzi
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę dobrać parametry transformaty w taki sposób, aby wykryć jak najwięcej
   komórek na obrazie, dbając jednocześnie o brak fałszywych segmentów.

## Detekcja konturów i ocena kształtu

Proszę uruchomić zadanie `Fruits.xml`

### Struktura zadania

   * **Source** - pobieranie danych z sensora
   * **HSVLut** - progowanie obrazu w przestrzeni HSV
   * **M[1/2/3]** - operatory morfologiczne
   * **Contours** - detekcja konturów
   * **Fruits** - ocena kształtów 
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę dobrać parametry progowania w taki sposób, aby wykrywane
   były jedynie żółte owoce
2. Dla dostępnych operatorów morfologicznych ustawić odpowiednie parametry
   tak, aby odfiltrować drobne segmenty i szum z poprzedniego kroku
3. Zaobserwować wartość parametru krągłości dla obiektów testowych w różnych 
   odległościach od kamery
4. Ustawić wartości parametru krągłości dla dwóch obiektów i przetestować 
   poprawność wykrywania
   

