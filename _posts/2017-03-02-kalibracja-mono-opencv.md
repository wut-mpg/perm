---
layout: task
title: Kalibracja kamery (1)
category: lab
lab: 1
task: 2
brief: Kalibracja parametrów wewnętrznych pojedynczej kamery - studium przypadku. W zadaniu wykorzystywany jest zbiór obrazów testowych.
---

## Informacje wstępne

Kalibracja parametrów wewnętrznych kamery (ogniskowa, współrzędne przecięcia osi optycznej z matrycą, współczynniki zniekształceń optycznych) możę być przeprowadzona
z wykorzystaniem znanego wzorca kalibracyjnego. Jednymi z częściej wykorzystywanych wzorców są szachownice o znanym rozmiarze. Znając współrzędne wierzchołków 
szachownicy w rzeczywistości (względem jednego z jej narożników) oraz odpowiadające im współrzędne w obrazie można przeprowadzić proces optymalizacji, który wyznaczy 
poszukiwane parametry. 

Jakość uzyskanych wyników w znacznej mierze zależy od pokrycia pomiarami całej przestrzeni obrazu, a także od dokładności lokalizacji wierzchołków wzorca testowego w obrazie.

## Uruchomienie zadania

Proszę uruchomić zadanie `CalibrateSequence.xml` z katalogu zadań PERM. Na ekranie powinny pojawić się dwa okna z obrazami - jedno z nich pokazuje obraz wejściowy wraz z nałożonym znalezionym wzorcem, drugie obraz po usunięciu zniekształceń optycznych.

![]({{site.url}}/public/l1/t1_1.png)

## Struktura zadania

   * **Sequence** - odczytywanie obrazów z dysku
      * *onLoadNextImage* - załaduj następny obraz
   * **CameraInfo** - ustawianie/odczytywanie obliczonych parametrów kamery
      * *camera_matrix* - bieżąca macierz kamery
      * *dist_coeffs* - bieżące parametry zniekształceń optycznych
   * **Undistort** - usunięcie zniekształceń optycznych obrazu
      * *alpha* - współczynnik skalowania obrazu wyjściowego
   * **Chessboard** - lokalizacja wzorca kalibracyjnego (szachownica) w obrazie
      * *board_width*, *board_height* - wymiary szachownicy
      * *square_width*, *square_height* - wymiary pojedynczego pola szachownicy
   * **Calib** - kalibracja parametrów kamery na podstawie zestawu danych pomiarowych
      * *clear_dataset* - wyczyść wszystkie zapamiętane obiekty
      * *add_Object3D* - zapamiętaj bieżący obiekt (szachownicę) 
      * *perform_calibration* - przeprowadź kalibrację na podstawie zapamiętanych pomiarów
   * **Window** - wyświetlanie obrazów

## Do zrobienia

1. Przeprowadzić kalibrację kamery na podstawie dostarczonych danych pomiarowych. 
Dla każdego poprawnie wykrytego wzorca kalibracyjnego dodać nowy pomiar w komponencie `Calib`.
2. Po zebraniu wszystkich pomiarów i przeprowadzeniu kalibracji odczytać wyliczone parametry kamery z komponentu `CameraInfo`.
3. Zmieniając współczynnik `alpha` w komponencie `Undistort` można zaobserwować wielkość zniekształceń optycznych.
4. Jak bardzo zmienią się wyniki, jeśli kalibracja przeprowadzona zostanie z użyciem mniejszej liczby obrazów?

## Do poczytania
   * Rozdział 11: _Camera models and calibration_ (str. 270-404) z książki _Learning OpenCV. Computer Vision with the OpenCV Library_, Gary Bradski and Adrian Kaehler, O'Reilly Media, 2008
   * OpenCV reference manual: [Camera Calibration and 3D Reconstruction](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html)
      * [findChessboardCorners](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#findchessboardcorners)
      * [calibrateCamera](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#calibratecamera)
      * [undistort](http://docs.opencv.org/2.4/modules/imgproc/doc/geometric_transformations.html#undistort)
