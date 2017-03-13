---
layout: task
title: Short-Time Fourier Transform
category: lab
lab: 2
task: 4
brief: Zastosowanie STFT do analizy sygnałów o charakterystyce zmiennej w czasie.
---

{% comment %} https://www.freesound.org/s/177268/ {% endcomment %}

## Wprowadzenie

Przy sygnałach o charakterystykach zmiennych w czasie (takich jak chociażby mowa) analiza widma całego nagrania będzie niosła jedynie informacje 
o całkowitym udziale danych częstotliwości w nagraniu. Przy analizie mowy (a ogólniej dźwięku, ale też innych sygnałów) istotne są natomiast
pewne zależności czasowe oraz sekwencje występowania konkretnych częstotliwości. W tego typu zadaniach, zamiast analizować cały sygnał, dzieli
się go na ramki o ustalonej długości oraz stopniu nachodzenia na siebie, a następnie dla każdej z nich wyznacza się transformatę Fouriera.

## Wyznaczanie spektrogramów

Proszę pobrać przykładowy [plik audio]({{ site.baseurl }}/public/l2/funf.wav) i załadować go do tablicy ([audioread](https://www.mathworks.com/help/matlab/ref/audioread.html)). 
Plik zawiera nagranie jednego słowa (*fünf*) wypowiedzianego przez kobietę. 

![]({{ site.baseurl }}/public/l2/funf.png)

Po załadowaniu proszę wyznaczyć i wyświetlić spektrogram ([spectrogram](https://www.mathworks.com/help/signal/ref/spectrogram.html)). Zmieniając odpowiednio parametry
proszę zaobserwować związek pomiędzy wielkością okna a rozdzielczością wyznaczonego spektrum sygnału dla pojedynczego okna. Proszę spróbować uzyskać wyniki również dla
skrajnych wartości parametrów.

![]({{ site.baseurl }}/public/l2/s_16.png)
![]({{ site.baseurl }}/public/l2/s_256.png)
![]({{ site.baseurl }}/public/l2/s_1024.png)

## Analiza sygnału z sensora ultradźwiękowego

Jedną z metod pomiaru odległości do przedmiotów jest wykorzystanie sensorów ultradźwiękowych (tzw. *ping*). Wysyłają one krótką serię impulsów o częstotliwości
ultradźwiękowej, a następnie badając czas po jakim ich ech dotrze do odbiornika określają odległość do przeszkody. 

Dla czujnika wysyłającego 8 impulsów o długości 1ms i częstotliwości 40kHz proszę wyznaczyć odległość do przeszkody. Proszę wykorzystać przykładowy 
[zarejestrowany sygnał]({{ site.baseurl }}/public/l2/output.txt). Sygnał ma częstotliwość próbkowania 200kHz. 

Sygnał *ping*:
![]({{ site.baseurl }}/public/l2/4_1.png)
![]({{ site.baseurl }}/public/l2/4_2.png)

Zarejestrowane *echo*:
![]({{ site.baseurl }}/public/l2/4_3.png)
