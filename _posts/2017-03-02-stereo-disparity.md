---
layout: task
title: Wyznaczanie obrazu rozbieżności
category: lab
lab: 1
task: 5
brief: Układ stereo-kamery - wyznaczanie obrazu rozbieżności (<i>disparity map</i>) dla układu stereo
---

## Informacje wstępne

Posiadając dwa obrazy z kamery stereo, po ich wyprostowaniu w procesie rektyfikacji, możliwe jest wyznaczenie obrazu rozbieżności (_disparity map_).

![Źródło obrazu: "Current Advancements in Stereo Vision" Edited by Asim Bhatti, ISBN 978-953-51-0660-9, Publisher: InTech, 2012 under CC BY 3.0 license]({{site.url}}/public/l1/stereo-geom.jpg)

Mapa rozbieżności w każdym punkcie zawiera różnicę pomiędzy położeniem tego punktu w obrazie lewym i prawym (o ile jest możliwe jej wyznaczenie).
W ogólności sprawdzenie, który punkt w obrazie prawym odpowiada obrazowi lewemu jest zadaniem trudnym, można jednak zastosować kilka uproszczeń.
Posiadanie obrazóe po procesie rektyfikacji sprawia, że punkty obrazu odpowiadające temu samemu punktowi w przestrzeni znajdują się na jednej linii
epipolarnej (zazwyczaj poziomej). Dzięki temu poszukiwanie odpowiedników sprowadza się do przeszukania jedynie jednej linii obrazu.

## Uruchomienie zadania

Proszę uruchomić zadanie `StereoDisparity.xml` z katalogu zadań PERM. Na ekranie powinny pojawić się cztery okna z obrazami - 
w dwóch są prezentowane obrazy wejściowe z lewej i prawej kamery, w dwóch pozostałych obraz rozbieżności oraz maska poprawnych pikseli.

![]({{site.url}}/public/l1/stereo.png)

## Struktura zadania

   * **Source[L/R]** - odczytywanie obrazów z dysku odpowiednio lewej i prawej kamery
      * *onLoadNextImage* - załaduj następny obraz
   * **CameraInfo[L/R]** - ustawianie/odczytywanie obliczonych parametrów kamery
      * *camera_matrix* - bieżąca macierz kamery
      * *dist_coeffs* - bieżące parametry zniekształceń optycznych
   * **Undistort** - usunięcie zniekształceń optycznych obrazów
      * *alpha* - współczynnik skalowania obrazu wyjściowego
   * **StereoEstimator** - wyznaczanie obrazu rozbieżności na podstawie pary obrazów stereo
      * *minDisparity* - Minimum possible disparity value. Normally, it is zero but sometimes rectification algorithms can shift images, so this parameter needs to be adjusted accordingly.
      * *numDisparities* - Maximum disparity minus minimum disparity. The value is always greater than zero. In the current implementation, this parameter must be divisible by 16.
      * *SADWindowSize* - Matched block size. It must be an odd number >=1 . Normally, it should be somewhere in the 3..11 range.
      * *disp12MaxDiff* - Maximum allowed difference (in integer pixel units) in the left-right disparity check. Set it to a non-positive value to disable the check.
      * *preFilterCap* - Truncation value for the prefiltered image pixels. The algorithm first computes x-derivative at each pixel and clips its value by [-preFilterCap, preFilterCap] interval. The result values are passed to the Birchfield-Tomasi pixel cost function.
      * *uniquenessRatio* - Margin in percentage by which the best (minimum) computed cost function value should “win” the second best value to consider the found match correct. Normally, a value within the 5-15 range is good enough.
      * *speckleWindowSize* - Maximum size of smooth disparity regions to consider their noise speckles and invalidate. Set it to 0 to disable speckle filtering. Otherwise, set it somewhere in the 50-200 range.
      * *speckleRange* - Maximum disparity variation within each connected component. If you do speckle filtering, set the parameter to a positive value, it will be implicitly multiplied by 16. Normally, 1 or 2 is good enough.
   * **DepthRainbow** - kolorowanie obrazu rozbieżności 
      ![]({{site.url}}/public/l1/heatmap.png)
   * **Window** - wyświetlanie obrazów


## Do zrobienia

1. Dobrać parametry tak, aby uzyskany obraz różnicowy był możliwie pełny, jednocześnie minimalizując liczbę błednych dopasowań.

## Do poczytania
   * OpenCV reference manual: [Camera Calibration and 3D Reconstruction](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html)
      * [findChessboardCorners](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#findchessboardcorners)
      * [StereoSGBM](http://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#stereosgbm)
   * ROS wiki - [Choosing good stereo parameters](http://wiki.ros.org/stereo_image_proc/Tutorials/ChoosingGoodStereoParameters)
