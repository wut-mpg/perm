---
layout: task
title: Operacje obszarowe
category: lab
lab: 3
task: 2
brief: Operacje kontekstowe - splot, operatory morfologiczne i rankingowe.
---

## Informacje wstępne

W przypadku, kiedy do przetwarzania wykorzystywane jest otoczenie punktu, 
mamy do czynienia z operacjami kontekstowymi. Kontekst może być wykorzystany
na wiele różnych sposobów. W przypadku progowania, zamiast dobierania globalnej
wartości, można dla każdego punktu obrazu przeanalizować jego otoczenie i wybrać
wartość progu w zależności od średniej jasności w nim.

Inną operacją kontekstową jest splot, gdzie wynikowa wartość punktu jest
obliczana jako splot obrazu z pewną macierzą, zwaną jądrem splotu. 
Modyfikując jądro splotu można uzyskać wiele różnych efektów, takich jak
rozmycia, wyostrzenia, wyznaczenie krawędzi czy narożników. 

Zamiast splotu, w otoczeniu punktu można zastosować operacje rankingowe.
Najpopularniejszą z nich jest mediana, a więc wybranie środkowej z posortowanych
wartości. Mediana może być używana do usuwania szumu typu sól-pieprz, 
a w przeciwieństwie do operacji rozmycia nie powoduje wprowadzenia nowych
wartości w obrazie.

Operacje morfologiczne działają bazując na dwóch bazowych operatorach - erozji i dylacji.
Pierwszy z nich powoduje efektywne zwiększenie rozmiaru obszarów tła (piksele czarne, o wartości 0),
drugi odwrotnie - powiększa rozmiar obiektów (piksele białe, o wartości 255).
Rozmiar i kształt modyfikacji zależny jest od wybranego elementu strukturalnego.
Na podstawie tych operatorów tworzone są operatory wyższego rzędu. Dwa przykładowe
to otwarcie (erozja-dylacja) oraz zamknięcie (dylacja-erozja). Powodują one
odpowiednio zlikwidowanie czarnych dziur w białych obiektach i na odwrót. 
Innym efektem działania tych operatorów jest zaokrąglanie narożników oraz
skracanie linii.

## Progowanie adaptacyjne

Proszę uruchomić zadanie `AdaptiveThreshold.xml`

### Struktura zadania

   * **Sequence** - odczytywanie obrazów z dysku
   * **Threshold** - progowanie obrazu
      * `C` - wartość odejmowana od średniej w otoczeniu (lokalny próg)
      * `method` - sposób wyznaczania średniej w otoczeniu (klasyczna bądź ważona funkcją gaussowską)
      * `blockSize` - wielkość otoczenia do wyznaczania średniej 
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę dobrać parametry progowania adaptacyjnego tak, aby poprawnie przetworzyć obraz
   sprawiający problemy w poprzednim zadaniu.

## Wygładzanie obrazu

Proszę uruchomić zadanie `Smoothing.xml`

### Struktura zadania

   * **Source** - pobieranie danych z sensora
   * **Box** - rozmycie "pudełkowe", maska kwadratowa
   * **Gaussian** - rozmycie gaussowskie
   * **Median** - filtr medianowy
   * **Bilateral** - filtr bilateralny 
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę pokręcić parametrami różnych metod wygładzenia obrazu. Jakie są zalety
   i wady poszczególnych algorytmów?
   
## Operacje morfologiczne
   
Proszę uruchomić zadanie `Morph.xml`

### Struktura zadania

   * **Sequence** - wczytywanie danych z dysku
   * **Erode** - erozja
   * **Dilate** - dylacja
   * **Open** - otwarcie
   * **Close** - zamknięcie
   * **Window** - wyświetlanie obrazów
   
Każdy z operatorów posiada następujące parametry:

   * `element` - wybór kształtu elementu strukturalnego
   * `element_size` - rozmiar elementu strukturalnego (wynikowy rozmiar okna wynosi `2*elem_size+1`)
   * `iterations` - liczba powtórzeń działania operatora
   
### Do zrobienia

1. Proszę ustawić parametry operacji morfologicznych tak, żeby odfiltrować
   wszystkie małe obiekty, pozostawiając jedynie duże komórki. Niektóre operatory
   nadadzą się do tego zadania lepiej, inne gorzej. 
2. Uruchamiając zadanie `MorphCamera.xml` można zaobserwować działanie 
   operatorów morfologicznych dla obrazu kolorowego.


## Operatory krawędziowe

Proszę uruchomić zadanie `Edge.xml`

### Struktura zadania

   * **Source** - pobieranie danych z sensora
   * **Blur** - wstępne rozmycie obrazu
   * **Sobel** - obliczanie gradientów obrazu za pomocą operatora [Sobela](http://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/sobel_derivatives/sobel_derivatives.html)
   * **Scharr** - obliczanie gradientów obrazu za pomocą operatora [Scharra](http://docs.opencv.org/modules/imgproc/doc/filtering.html?highlight=scharr#scharr)
   * **Canny** - detekcja krawędzi przy pomocy detektora [Canny'ego](http://docs.opencv.org/2.4/doc/tutorials/imgproc/imgtrans/canny_detector/canny_detector.html)
   * **Window** - wyświetlanie obrazów

### Do zrobienia

1. Proszę zapoznać się z działaniem każdego z operatorów 
2. Przy operatorze Canny'ego proszę sprawdzić działanie obu progów histerezy



