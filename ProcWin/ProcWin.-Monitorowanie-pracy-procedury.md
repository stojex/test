# ProcWin. Monitorowanie pracy procedury
Wymagania:
- [ProcWin. Konfiguracja modułu](/ProcWin/ProcWin.-Konfiguracja-modułu.md) 
- [TODO: ProcWin. Definiowanie zmiennych]
- [TODO: ProcWin. Tworzenie procedur]


Pisząc procedurę chciałbyś mieć pewność, że jest zawsze wykonywana. Moduł ProcWin nie posiada obecnie wbudowanego mechanizmu monitorowania procedury. Może okazać się, że ktoś wyłączył moduł, procedura zatrzymała się z powodu braku wartości lub wystąpi inna sytuacja, która będzie powodować, że skrypt nie będzie działał. Niestety nie zostaniesz o tym powiadomiony jeśli sam o to nie zadbasz. 

Przyjrzyjmy się prostemu przykładowi: 
```
REMOTE ZMIENNA1 SERWER@ZMIENNA1
REMOTE ZMIENNA2 SERWER@ZMIENNA2
REMOTE TEST_PROCEDURE SERWER@TEST_PROCEDURE

SET TEST_PROCEDURE = 0
:BEGIN
SET TEST_PROCEDURE = 1
CALL CHECK_VALUE(ZMIENNA1)
SET TEST_PROCEDURE = 2
CALL CHECK_VALUE(ZMIENNA2)
SET TEST_PROCEDURE = 3
GOTO BEGIN

PROCEDURE CHECK_VALUE(SOURCE)
BEGIN
SLEEP 60
END
```
Skrypt zawiera procedurę CHECK_VALUE, która wykonuje operację czekaj przez 60 sekund. Procedura powinna robić to co potrzebujesz. Dla przykładu w zupełności wystarczy SLEEP. 

Na początku deklarujemy 3 zmienne. Dwie, na których będzie wykonywana operacja, a trzecia jest zmienną monitorującą procedurę. Dla każdej procedury musimy utworzyć osobną zmienną, dlatego warto pomyśleć o usystematyzowaniu nazw zmiennych. Kolejnym krokiem jest ustawianie wartości zmiennej monitorującej odpowiednimi wartościami. W powyższym przykładzie przed etykietą :BEGIN ustawiamy wartość TEST_PROCEDURE na 0. Dzięki temu, że jest to ustawiane przed sekcja, która będzie powtarzana, będziemy mieli informacje o czasie startu procedury. Zaraz za etykietą, a przed wykonaniem pierwszego wywołania procedury CHECK_VALUE ustawiamy wartość 1. Następnie w zależności od potrzeb i ilości wywołań procedury dopasowujemy wartości ustawiane na zmiennej TEST_PROCEDURE. Zlecam jednak zwiększanie wartości maksymalnie do wartości 5-10 w zależności od szybkości wykonania procedury CHECK_VALUE. Jeśli w jednym skrypcie procedura wywoływana jest 100 razy lepiej zmieniać wartość zmiennej np. co 10 wywołań, lub przenieść ustawianie wartości do procedury. Jedno ustawienie na początek, drugie na koniec np.
```
PROCEDURE CHECK_VALUE(SOURCE)
BEGIN
SET TEST_PROCEDURE = 1
SLEEP 60
SET TEST_PROCEDURE = 2
END
```
Najważniejsze założenie jest takie, by wartość zmiennej TEST_PROCEDURE wracała do wartości 1 w sensownym czasie np. 1-5 minut. Im krótszy czas, tym szybciej będziemy mieli informacje o wystąpieniu problemu z procedurą.

Mamy już zmienną, czas na przygotowanie alarmu. Zmienna będzie charakteryzowała się wartościami zwiększanymi do określonej wartości i powrót do 1. Np. [0,1,2,3,4,1,2,3,4,1,2,3,4]. Musimy przygotować dwa (lub trzy) alarmy. Pierwszy alarm powinien być ustawiony z warunkiem = 1 i opóźnieniem wystąpienie alarmu np. 120 [s]. Czas należy dobrać tak, by wykonanie cyklu procedury zdążyło się bez problemu wykonać. Drugi alarm tworzymy z warunkiem > 1 i opóźnieniem wystąpienie alarmu np. 120 [s]. Możemy teraz te 2 alarmy wrzucić do TelView, lub przygotować jeden zbiorczy typu OR dla tych dwóch alarmów. 

[Powrót do listy](/README.md)