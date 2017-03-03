---
layout: task
title: Kalibracja pary stereo
category: lab
lab: 1
task: 4
brief: Układ stereo-kamery - kalibracja parametrów wewnętrznych oraz zewnętrznych (wzajemne położenie) obu kamer.
---

## Informacje wstępne

Układ, w którym obraz pozyskiwany jest jednocześnie z dwóch kamer skierowanych w tę samą stronę, nazywany jest parą stereo.
Przesunięcie pomiędzy osiami optycznymi kamer (zwane *baseline*) odpowiada w tym układzie rozstawowi ludzkich oczu.
Kalibracja układu kamer stereo, oprócz wyznaczenia parametrów wewnętrznych każdej z kamer, określa też ich wzajemne położenie
(np. traktując lewą kamerę jako punkt odniesienia), czyli translację oraz rotację. 

![Źródło obrazu: "Current Advancements in Stereo Vision" Edited by Asim Bhatti, ISBN 978-953-51-0660-9, Publisher: InTech, 2012 under CC BY 3.0 license]({{site.base_url}}/public/l1/stereo-geom.jpg)

Kalibracja układu stereo może być dokonana jako jedno duże zadanie optymalizacyjne (kilkadziesiąt zmiennych do optymalizacji)
bądź w trybie dwukrokowym, gdize najpierw kalibrowane sa niezależnie parametry wewnętrzne obu kamer, a następnie, znając je,
optymalizowane jest wzajemne położenie obu kamer. 

Poprawnie skalibrowana para stereo pozwala na przeprowadzenie procesu rektyfikacji obrazu, czyli takiego przekształcenia, 
po którym oba obrazy sprowadzane są do wspólnego punktu widzenia (tak, aby te same punkty przestrzeni widziane w obu kamerach
znajdowały się na tej samej wysokości).

## Uruchomienie zadania

Proszę uruchomić zadanie `CalibrateStereo.xml` z katalogu zadań PERM. Na ekranie powinny pojawić się cztery okna z obrazami - 
w dwóch są prezentowane obrazy wejściowe z lewej i prawej kamery, w dwóch pozostałych te same obrazy po usunięciu zniekształceń.

## Struktura zadania

   * **Source[L/R]** - odczytywanie obrazów z dysku odpowiednio lewej i prawej kamery
      * *onLoadNextImage* - załaduj następny obraz
   * **CameraInfo[L/R]** - ustawianie/odczytywanie obliczonych parametrów kamery
      * *camera_matrix* - bieżąca macierz kamery
      * *dist_coeffs* - bieżące parametry zniekształceń optycznych
   * **Undistort** - usunięcie zniekształceń optycznych obrazów
      * *alpha* - współczynnik skalowania obrazu wyjściowego
   * **Chessboard[L/R]** - lokalizacja wzorca kalibracyjnego (szachownica) w obrazie
      * *board_width*, *board_height* - wymiary szachownicy
      * *square_width*, *square_height* - wymiary pojedynczego pola szachownicy
   * **Calib** - kalibracja parametrów kamery na podstawie zestawu danych pomiarowych
      * *clear_dataset* - wyczyść wszystkie zapamiętane obiekty
      * *add_Object3D* - zapamiętaj bieżący obiekt (szachownicę) 
      * *perform_calibration* - przeprowadź kalibrację na podstawie zapamiętanych pomiarów
   * **Window** - wyświetlanie obrazów

## Do zrobienia

1. Przeprowadzić kalibrację pary stereo na podstawie dostarczonych danych pomiarowych. 
Dla każdego poprawnie wykrytego wzorca kalibracyjnego dodać nowy pomiar w komponencie `Calib`
(proszę zwrócić uwagę na to, czy wzorzec wykryty jest w obu obrazach jednocześnie).
2. Po zebraniu wszystkich pomiarów proszę przeprowadzić kalibrację układu w dwóch trybach (tryb kalibracji dwukrokowej `two_step`).
  Proszę porównać wyniki kalibracji dla obu przypakdów, a także porównać je z wynikami uzyskanymi w pierwszym zadaniu
  (gdzie kalibrowane były parametry wewnętrzne lewej kamery).
3. Zmieniając współczynnik `alpha` w komponencie `Undistort` można zaobserwować wielkość zniekształceń optycznych.
4. Proszę zapisać kalibrację obu kamer (lewej i prawej) do pliku - wywołać zdarzenie `save_file` w obu komponentach.

## Do poczytania
   * Rozdział 11: _Camera models and calibration_ (str. 270-404) z książki _Learning OpenCV. Computer Vision with the OpenCV Library_, Gary Bradski and Adrian Kaehler, O'Reilly Media, 2008
   * OpenCV reference manual: [Camera Calibration and 3D Reconstruction](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html)
      * [findChessboardCorners](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#findchessboardcorners)
      * [stereoCalibrate](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#stereocalibrate)
      * [stereoRectify](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#stereorectify)
