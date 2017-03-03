---
layout: task
title: Wprowadzenie do DisCODe
category: lab
lab: 1
task: 1
brief: Celem pierwszego zadania jest zapoznanie z oprogramowaniem DisCODe - uruchamianie GUI, startowanie i zatrzymywanie zadań oraz zmiana ich parametrów.
---

## Struktura katalogów

Istotne (z punktu widzenia wykonywanych zadań) katalogi przedstawione zostały w poniższej tabeli:

| Katalog | Opis |
| --- | --- |
| /opt | |
| /opt/**discode** | główny katalog programu |
| /opt/discode/**DCL** | katalog zawierający biblioteki komponentów i zadań |
| /opt/discode/DCL/**CvCoreTypes** | Dane wspólne dla wszystkich bibliotek związanych z przetwarzaniem obrazów |
| /opt/discode/DCL/**CvBasic** | Podstawowe komponenty do przetwarzania obrazu |
| /opt/discode/DCL/**CvStereo** | Komponenty związane z kalibracją i obsługą obrazu z kamer stereo |
| /opt/discode/DCL/**perm** | Percepcja Maszyn |
| /opt/discode/DCL/perm/**tasks** | Zadania |
| /opt/discode/DCL/perm/**data** | Dane testowe |


## Uruchamianie interfejsu graficznego DisCODe

Interfejs graficzny DisCODe (`discode_gui`) pozwala na uruchamianie i zatrzymywanie zadań a także na zmianę ich parametrów w trakcie działania. Aby go uruchomić, w terminalu należy wydać kolejno polecenia:

{% highlight bash %}
source /opt/discode/setup.bash
discode_gui
{% endhighlight %}

Na ekranie powinno pojawić się główne okno programu:
![]({{ site.base_url }}/public/l1/gui.png)

## Uruchomienie zadania

Po wybraniu opcji `Spawn` można wybrać z dysku zadanie do uruchomienia. Proszę wybrać zadanie `SequenceViewer.xml` z katalogu `/opt/discode/DCL/perm/tasks`.

![]({{ site.base_url }}/public/l1/spawn.png)

Po uruchomieniu zadania (należy ponownie nacisnąć przycisk `Spawn`) w oknie powinien pojawić się spis uruchomionych komponentów, a dodatkowo powinno wyświetlić się okno ze zmieniającymi się obrazami testowymi.

![]({{ site.base_url }}/public/l1/sequence.png)

## Zmiana parametrów zadania

Po lewej stronie okna znajduje się lista uruchomionych komponentów. Po wybraniu jednego z nich w prawej części wyświetlą się parametry z nim związane. Po wybraniu komponentu `Sequence` można odznaczyć opcję `auto_next_image`, przez co obrazy przestaną się przełączać. 

Przyciski w dolnej części okna pozwalają na wyzwalanie zdarzeń związanych z komponentami. Wywołanie zdarzenia `Next image` spowoduje przełączenie na kolejny obraz.

## Zatrzymywanie zadania

Na pasku narzędzi dostępne są dwa przyciski:

| ![]({{ site.base_url }}/public/l1/disconnect.png) | Odłączenie od działającego zadania |
| ![]({{ site.base_url }}/public/l1/exit.png) | Zakończenie działającego zadania |

**Odłączenie** interfejsu użytkownika od uruchomionego zadania pozwala na pozostawienie zadania działającego w tle. W celu ponownego podłączenia do tego zadania należy w głównym oknie programu wybrać opcję `Connect`.

**Zakończenie** zadania powoduje wysłanie do działającego procesu sygnału zakończenia, który po chwili powoduje jego zamknięcie. 
