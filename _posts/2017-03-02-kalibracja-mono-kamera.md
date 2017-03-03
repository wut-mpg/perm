---
layout: task
title: Kalibracja kamery (2)
category: lab
lab: 1
task: 3
brief: Kalibracja parametrów wewnętrznych pojedynczej kamery - testy na sprzęcie, wykorzystanie różnych wzorców kalibracyjnych.
---

## Uruchomienie zadania

W zależności od podłączonej do komputera kamery oraz zastosowanego wzorca testowego, należy uruchomić odpowiednie zadanie. 

| **Sensor**              | **Zadanie**           |
| Kinect + szachownica    | `CalibrateKinectChessboard.xml` |
| Kinect + kropki         | `CalibrateKinectdots.xml` |
| PS Eye + szachownica    | `CalibrateCameraChessboard.xml` |
| PS Eye + kropki         | `CalibrateCameraDots.xml` |

Po uruchomieniu na ekranie powiny pojawić się dwa okna z obrazem, podobnie jak w zadaniu poprzednim.

## Struktura zadania

   * **Source** - odczytywanie obrazów z sensora
   * **CameraInfo** - ustawianie/odczytywanie obliczonych parametrów kamery
      * *camera_matrix* - bieżąca macierz kamery
      * *dist_coeffs* - bieżące parametry zniekształceń optycznych
   * **Undistort** - usunięcie zniekształceń optycznych obrazu
      * *alpha* - współczynnik skalowania obrazu wyjściowego
   * **Pattern** - lokalizacja wzorca kalibracyjnego (szachownica lub kropki) w obrazie
      * *board_width*, *board_height* - wymiary szachownicy
      * *square_width*, *square_height* - wymiary pojedynczego pola szachownicy
      * *grid.width*, *grid.height*, *grid.size* - wymiary wzorca kołowego
   * **Calib** - kalibracja parametrów kamery na podstawie zestawu danych pomiarowych
      * *clear_dataset* - wyczyść wszystkie zapamiętane obiekty
      * *add_Object3D* - zapamiętaj bieżący obiekt (szachownicę) 
      * *perform_calibration* - przeprowadź kalibrację na podstawie zapamiętanych pomiarów
   * **Window** - wyświetlanie obrazów

Poniżej znajduje się wyjaśnienie parametrów dla obu wzorców kalibracyjnych.

![]({{site.baseurl}}/public/l1/pattern_explained.png)

## Do zrobienia

1. Przeprowadzić kalibrację kamery z wykorzystaniem obu wzorców testowych (osobno dla szachownicy, osobno dla kropek).
Dla każdego poprawnie wykrytego wzorca kalibracyjnego dodać nowy pomiar w komponencie `Calib`.
W czasie kalibracji proszę starać się pokryć pomiarami całą powierzchnię obrazu, jak również różne odległości od sensora.
2. Po zebraniu wszystkich pomiarów i przeprowadzeniu kalibracji odczytać wyliczone parametry kamery z komponentu `CameraInfo`.
3. Porównać wyniki kalibracji uzyskane dla obu wzorców.
4. Proszę wybrać sobie jakiś prosty obiekt (np. piłka). Proszę dokonać _ręcznej_ lokalizacji obiektu w przestrzeni kamery:
   * należy zmierzyć fizyczny wymiar obiektu (np. średnicę)
   * pokazać obiekt do kamery i zapisać obraz na dysku
   * otworzyć obraz w programie graficznym (np. Gimp) i zmierzyć wybrany wymiar w obrazie (w pikselach)
   * na podstawie wyznaczonych parametrów wewnętrznych kamery i obu pomiarów obliczyć odległość obiektu od kamery

## Do poczytania
   * Rozdział 11: _Camera models and calibration_ (str. 270-404) z książki _Learning OpenCV. Computer Vision with the OpenCV Library_, Gary Bradski and Adrian Kaehler, O'Reilly Media, 2008
   * OpenCV reference manual: [Camera Calibration and 3D Reconstruction](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html)
      * [findChessboardCorners](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#findchessboardcorners)
      * [findCirclesGrid](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#findcirclesgrid)
      * [calibrateCamera](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#calibratecamera)
      * [undistort](http://docs.opencv.org/2.4/modules/imgproc/doc/geometric_transformations.html#undistort)
