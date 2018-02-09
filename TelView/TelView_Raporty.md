# TelView - Raporty
Raporty umożliwiają sprawne tworzenie zestawów danych raportowych, prezentowanych w formie tabularycznej. Na raporcie tym mogą być prezentowane dane bieżące, archiwalne, raportowe: godzinowe, dobowe, miesięczne i okresowe.

## Tworzenie raportu
Przygotowanie raportu sprowadza się do sparametryzowania opcji i listy zmiennych, które będą prezentowane w trybie prezentacji danych. Okno edycyjne raportu prezentuje się następująco:
![Okno raportu](/TelView/img/TelView_Raporty_Okno_Edycji.png)

Przejdziemy teraz po wszystkich elementach okna edycji i zobaczymy jak te opcje wpływają na wygląd naszego raportu.

#### Tytuł
Parametr Tytuł pozwala na zdefiniowanie tytułu okna, który zostanie wyświetlony w trybie prezentacji danych.
![Tytuł okna raportu](/TelView/img/TelView_Raporty_Okno_Edycji_Tytuł_Okna.png)

#### Typ danych
Parametr Typ danych określa rodzaj prezentowanych danych (bieżące, archiwalne, godzinowe, dobowe, miesięczne, okresowe). Dla wartości archiwanych należy dodatkowo zdefiniować w polu Okres archiwizacji czas (w minutach).

Na poniższych zrzutach zaprezentowałem jak zmieniają się opcję dostępne dla poszczególnych typów danych. Dla wartości bieżących dostępnych opcji jest najmniej. Działanie poszczególnych opcji wyjaśnione jest w dalszej części dokumentu.
![Typ danych: bieżące](/TelView/img/TelView_Raporty_Okno_Edycji_Typ_Danych_bieżące.png)

Dla danych archiwalnych musimy zdefiniować okres archiwizacji. Jeśli w module TelSrv mamy zdefiniowaną archiwizację częstszą np. co 1 minutę, to raport ten będzie agregował te dane do np. 5 minut w sposób wybrany w [Funkcji archiwów](/TelView/TelView_Raporty.md#funkcja-archiw%C3%B3w).
![Typ danych: archiwalne](/TelView/img/TelView_Raporty_Okno_Edycji_Typ_Danych_archiwalne.png)

Dla danych raportowych opcje są identyczne dla każdego typu danych. Dla danych raportowych pojawia nam się dodatkowa opcja [Dowolny zakres danych](/TelView/TelView_Raporty.md#dowolny-zakres-danych).
![Typ danych: raportowe](/TelView/img/TelView_Raporty_Okno_Edycji_Typ_Danych_raportowe.png)

#### Dowolny zakres danych

Parametr Dowolny zakres danych definiuje zakres prezentowania danych w trybie prezentacji. Zaznaczenie opcji spowoduje w trybie prezentacji wyświetlenie dwóch pól umożliwiających wybranie początku i końca okresu. W przeciwnym razie dane będą prezentowane w domyślnym zakresie. Dla danych godzinowych będzie to doba, dla dobowych i okresowych – miesiąc, a dla danych miesięcznych – rok.

#### Godzina bazowa
W niektórych branżach (np. gazowniczej) doba rozumiana jest jako czas w godzinach 6:00 do godziny 6:00 następnego dnia. By raporty uwzględniały taką definicję doby została wprowadzona opcja "Godzina bazowa". Parametr Godzina bazowa pozwala na zdefiniowanie początkowej godziny doby. Opcja ta będzie dostępna wyłącznie dla danych raportowych godzinowych i przy wyłączonej opcji Dowolny zakres danych.  

Przykładowe uruchomienie schematu z godziną bazową 0. Jest to wartość domyślna.
![Godzina bazowa 0](/TelView/img/TelView_Raporty_Okno_Edycji_Godzina_bazowa_0.png)
Przykładowe uruchomienie schematu z godziną bazową 6. Raport zostanie otworzony w zakresie od godziny 6:00 do godziny 5:00 następnego dnia.
![Godzina bazowa 6](/TelView/img/TelView_Raporty_Okno_Edycji_Godzina_bazowa_6.png)
W branży gazowniczej 1 lipca 2012 roku zmieniła się definicja doby gazowej z godziny 22-22 na godzinę 6-6. W związku z tym w systemie TelWin SCADA została wprowadzona automatyczna opcja zmiany godziny bazowej 22 na godzinę 6. Dlatego tak zdefiniowany raport otworzy się na godzinę 6 rano. Opcja jest automatycznie zaznaczona.
![Godzina bazowa 22](/TelView/img/TelView_Raporty_Okno_Edycji_Godzina_bazowa_22.png)

#### Poziom uprawnień lub grupa użytkowników
Parametr Poziom uprawnień lub grupa użytkowników pozwala na ograniczenie dostępu do raportu, dla użytkowników mających niewystarczający poziom uprawnień lub nie należących do podanej grupy lokalnej. Raport będzie dostępny tylko dla użytkowników posiadających poziom uprawnień równy lub wyższy od wymaganego dla danego raportu. Wprowadzenie poziomu uprawnień 0 spowoduje udostępnienie danego raportu wszystkim użytkownikom.

## Dostępne zmienne
Grupa parametrów Dostępne zmienne pozwala na wyświetlenie drzewa zmiennych dla wybranego Źródła. Włączenie parametru Filtr uaktywni dwa pola edycyjne Nazwa i Opis umożliwiające wprowadzenie wzorców filtrowania prezentowanego drzewa zmiennych. Wzorzec może zawierać znak „*” symbolizujący wystąpienie dowolnego ciągu znaków (także pustego) lub znak „?” symbolizujący wystąpienie jednego znaku. Zaznaczenie zmiennej, a następnie naciśnięcie przycisku Dodaj spowoduje przeniesienie zmiennej do grupy parametrów Wybrane zmienne (zmienna może zostać dodana do listy wielokrotnie). Istnieje również łatwiejszy sposób dodawania zmiennych poprzez ich zaznaczenie a następnie przeciągnięcie (drag & drop) za lub przed odpowiedni wiersz danych w tabelce Wybrane zmienne.



## Wybrane zmienne
Grupa parametrów Wybrane zmienne pozwala na modyfikację parametrów listy zmiennych, które będą wyświetlane w trybie prezentacji danych. Dla każdej zmiennej istnieje możliwość zmiany Nazwy pełnej, Mnożnika, Formatu, Funkcji i Czcionki eksportu poprzez zaznaczenie lewym przyciskiem myszy wybranego pola. Zaznaczenie jednej lub wielu linii na liście, a następnie naciśnięcie przycisku Usuń na okienku lub Delete na klawiaturze spowoduje usunięcie zaznaczonych zmiennych z listy. Położenie grupy lub pojedynczych zmiennych można zmieniać albo przez użycie przycisków W górę i W dół albo za pomocą skrótu klawiszowego: prawy ALT + strzałka w górę / w dół. Zaznaczenie wszystkich wierszy tabelki odbywa się za pomocą skrótu CTRL + A. Zaznaczenie wielu pojedynczych elementów na liście, a następnie naciśnięcie przycisku Grupuj/Rozgrupuj spowoduje utworzenie z tych zmiennych grupy z unikalnym identyfikatorem. Zdefiniowanie Nazwy pełnej dla grupy umożliwi prezentację w trybie uruchomieniowym raportu nazwy zamiast identyfikatora. Zaznaczenie elementu grupowego i naciśnięcie przycisku Grupuj/Rozgrupuj spowoduje rozgrupowanie elementów należących do grupy. Funkcjonalność zawarta pod przyciskiem Aktualizuj dane, zapewnia wypełnienie pól Nazwa pełna oraz Opis aktualnymi danymi z serwera. Należy w tym miejscu wspomnieć o sytuacji szczególnej; pole "Nazwa pełna" zmiennej nie jest aktualizowana jeżeli jest pusta po stronie serwera.

![Wybrane zmienne](/TelView/img/TelView_Raporty_Okno_Edycji_Wybrane_Zmienne.png)

Kolumny tworzące listę wybranych zmiennych:
#### Źródło
Parametr *Źródło* prezentuje nazwę serwera, z którego pobierana jest zmienna.

#### Nazwa
Parametr *Nazwa* prezentuje nazwę zmiennej.

#### Nazwa pełna
Parametr *Nazwa pełna* może być automatycznie wypełniany w trybie uruchomieniowym raportu:
nazwą pełną z definicji zmiennej, jeśli w polu zostanie wpisany znak tyldy "~"
zdefiniowanym tekstem, w którym możemy korzystać z następujących parametrów:

- %NAME% - uzupełniany nazwą zmiennej,
- %SRC% - uzupełniany źródłem zmiennej,
- %DESC% - uzupełniany opisem zmiennej.

#### Mnożnik
Wartość w kolumnie *Mnożnik* będzie brana pod uwagę w trybie uruchomieniowym na dwa sposoby. Pierwszy z nich dotyczy przemnożenia otrzymanych wartości ze źródła danych przez bezwzględną wartość mnożnika (nie będzie brany pod uwagę znak ‘-‘ przed wartością mnożnika). Drugi sposób dotyczy wyliczenia wartości grupy. Znak ‘-‘ będzie decydował, czy wartość elementu zostanie dodana do grupy, czy też odjęta od niej.

#### Przesunięcie
Wartość w kolumnie *Przesunięcie* spowoduje dodanie tej wartości do wartości zmiennej. Jeśli liczba będzie poprzedzona znakiem "-" wartość prezentowana będzie pomniejszona.

#### Format
Kolumna *Format* pozwala na zdefiniowanie formatu wyświetlania wartości w trybie uruchomieniowym. Zasada jest identyczna jak w przypadku elementu Pomiar. Wartość 10 oznaczać będzie, że liczba będzie wyświetlona przez maksymalnie dziesięć cyfr. Wartość 8.2 oznaczać, będzie liczbę składającą się z pięciu cyfr i dwóch po przecinku (jeden znak zostanie wykorzystany jako separator liczby).

#### Funkcja
Kolumna Funkcja.

#### Funkcja grupy
Kolumna Funkcja grupy.

#### Funkcja archiwów
> Tutaj opis

#### Czcionka
Kolumna *Czcionka* eksportu pozwala na wybranie czcionki, która zostanie wykorzystana podczas eksportu prezentowanych wartości do arkusza kalkulacyjnego Microsoft Excel.

### Edycja listy wybranych zmiennych. 
Za pomocą menu kontekstowego na liście wybranych zmiennych istnieje możliwość kopiowania, wklejania, usuwania, blokowania/odblokowywania modyfikacji wartości w trybie podglądu danych raportowych, grupowego modyfikowania parametrów zmiennych raportu i importu zmiennych z pliku: 

Wywołanie funkcji Zmiana parametrów spowoduje wywołanie okna dialogowego umożliwiającego modyfikację parametrów dla zaznaczonych wierszy na liście wybranych zmiennych. 

Przed wywołaniem okna następuje analiza zaznaczonych zmiennych. Jeżeli parametr powtórzy się we wszystkich zaznaczonych zmiennych, zostanie on zablokowany. Za pomocą przycisku Odblokuj parametry można zresetować okno dialogowe i odblokować wszystkie parametry. 

Wywołanie funkcji Import zmiennych z pliku spowoduje otwarcie okna dialogowego do wyboru pliku w formacie TXT, z którego zostaną zaimportowane zmienne. Importowane parametry: 
- źródło 
- zmienna 

Format odczytu danych z pliku tekstowego: parametry odzielone znakiem tabulacji, np.
Targi[TAB]PP1 



## Parametry prezentacji listy wybranych zmiennych
#### Podsumowanie
Parametr Podsumowanie umożliwia wybranie jednej z funkcji podsumowujących dane w trybie prezentacji.

#### Format etykiety czasowej
Parametr Format etykiety czasowej kolumn pozwala na zmianę domyślnego formatu etykiety czasowej kolumn wyświetlających dane (%d-%m-%Y |%H:%M). Pionowa kreska oznacza podział etykiety i wyświetlenie jej w dwóch liniach.

#### Wyróżnianie braku kompletności wartości raportowej
Parametr Wyróżnianie braku kompletności wartości raportowej umożliwia włączenie/wyłączenie wyświetlenia braku kompletności wartości raportowej, w postaci zmiany koloru tekstu dla wartości niekompletnej.

#### Automatyczne aktualizowanie wprowadzonej wartości raportowej
Parametr *Automatyczne aktualizowanie wprowadzonej wartości raportowej* umożliwia włączenie/wyłączenie automatycznego przesyłania zmodyfikowanej wartości do źródła. W przypadku wyłączenia opcji, użytkownik, w celu przesłania wprowadzonej wartości do źródła, musi ręcznie uruchomić mechanizm aktualizowania przy pomocy przycisku znajdującego się na pasku narzędziowym raportu.

#### Transpozycja tabeli
Parametr Transpozycja tabeli umożliwia włączenie/wyłączenie transpozycji (zamianę wierszy i kolumn) prezentowanych danych raportowych.
![Transpozycja tabeli](/TelView/img/TelView_Raporty_Okno_Edycji_Transpozycja_tabeli.png)

#### Ukrywanie kolumny z opisem
Parametr Ukrywanie kolumny z opisem umożliwia ukrycie tej kolumny w trybie prezentacji.

#### Ukrywanie statusu wartości
Parametr Ukrywanie statusu wartości umożliwia włączenie/wyłączenie wyświetlania statusów wartości.

#### Eksport wartości bez statusów
//TODO: Opis

#### Ignorowanie wartości nieznanych
Parametr Ignorowanie wartości nieznanych spowoduje ignorowanie nieznanych wartości podczas liczenia wartości określonych przez funkcje.

#### Odwrócenie osi czasu
Parametr Odwrócenie osi czasu umożliwia wyświetlenie danych w odwróconej kolejności względem czasu (od najpóźniejszych do najwcześniejszych).
![Odwrócenie osi czasu](/TelView/img/TelView_Raporty_Okno_Edycji_Odwrócenie_Osi_Czasu.png)

#### Ukrywanie wierszy z wartościami nieznanymi
Parametr Ukrywanie wierszy z wartościami nieznanymi umożliwia włączenie/wyłączenie wyświetlenia danych bez wierszy, które w całości składają się z wartości nieznanych.

#### Kontrola danych raportowych
Grupa parametrów Kontrola danych raportowych pozwala na zdefiniowanie Dopuszczalnej różnicy (wyrażonej w procentach), o którą mogą różnić się dwie sąsiednie wartości raportowe. W przypadku przekroczenia różnicy wartość zostanie wyróżniona Kolorem po przekroczeniu. Zaznaczenie opcji Automatyczna kontrola spowoduje sprawdzenie raportu po każdorazowej zmianie parametru Dopuszczalna różnica w trybie prezentacji danych lub aktualizacji raportu.


#### Przekaż datę schematu i tryb przeglądania
//TODO: Opis


>UWAGA!!!
>Zaznaczenie wiersza na liście wybranych zmiennych, a następnie dodanie lub wstawienie nowej zmiennej z listy dostępnych zmiennych, spowoduje dodanie nowej zmiennej z parametrami zmiennej zaznaczonej.


## Tryb prezentacji. 
W trybie prezentacji danych raport będzie wyświetlony zależnie od zdefiniowanego parametru Dowolny zakres danych i parametrów z grupy Kontrola danych raportowych zdefiniowanych w trybie edycji. 


Powyższe okno prezentuje pobrane dane raportowe bez włączonej opcji Dowolny zakres danych i włączoną automatyczną kontrolą danych raportowych. Za pomocą przycisków znajdujących się w lewym, górnym rogu okna istnieje możliwość zmiany zakresu prezentowanych danych o domyślny okres dla danego typu danych. Dla raportów godzinowych będzie to doba, dla dobowych i okresowych – miesiąc, a dla miesięcznych – rok. Przyciski z ikonami umożliwiają: eksport prezentowanych danych do formatu PDF, eksport do programu Microsoft Excel, eksport do formatu CSV, eksport do formatu TXT, włączenie/wyłączenie transpozycji eksportowanej tabeli (spowoduje zamianę wierszy i kolumn w tabeli prezentowanych danych raportowych), wydruk raportu oraz włączenie/wyłączenie ukrywania wierszy z wartościami nieznanymi. Zmiana parametru Dopuszczalna różnica spowoduje automatyczne sprawdzenie raportu i wyróżnienie kolorem tych wartości, które względem sąsiednich przekraczają procentowo dopuszczalną różnicę. 



Powyższe okno prezentuje pobrane dane raportowe z włączoną opcją Dowolny zakres danych i wyłączoną automatyczną kontrolą danych raportowych. Za pomocą pól z datami istnieje możliwość zdefiniowania początku i końca okresu prezentowania danych raportowych. Po zmianie którejkolwiek z dat uaktywniony zostanie przycisk Pobranie, za pomocą którego użytkownik może zainicjować pobranie danych raportowych z wybranego zakresu. Przyciski z ikonami umożliwiają: eksport prezentowanych danych do formatu PDF, eksport do programu Microsoft Excel, eksport do formatu CSV, eksport do formatu TXT, włączenie/wyłączenie transpozycji tabeli (spowoduje zamianę wierszy i kolumn w tabeli prezentowanych danych raportowych i podczas eksportu danych), wydruk raportu oraz włączenie/wyłączenie ukrywania wierszy z wartościami nieznanymi. Zmiana parametru Dopuszczalna różnica musi być zaakceptowana naciśnięciem przycisku powodującego weryfikację danych raportowych. 

W trybie prezentacji danych istnieje możliwość modyfikowania lub wprowadzania wartości raportowych. Aby zablokować/odblokować modyfikowanie wartości raportowych służy opcja "Blokowanie/odblokowywanie mod. wartości". Ręczna zmiana wartości powoduje jednocześnie zablokowanie zmiennej (status Blokada). Naciśnięcie na klawiaturze numerycznej klawisza *, w fazie wprowadzania danych, spowoduje skasowanie wartości wprowadzonej przez operatora (tzw. nastawy ręcznej). Naciśnięcie na klawiaturze znaku „$” (Shift+4), w fazie wprowadzania danych, spowoduje ustawienie wartości nieznanej ze statusem blokada. 

Dane raportowe mogą zostać posortowane według kolumny. Wynikiem jest posortowana lista od A do Z lub od Z do A. By posortować wartości raportowe należy kliknąć na nazwę kolumny, według której dane mają być posortowane, kolejne kliknięcie odwraca porządek sortowania. 

Kolejnym udogodnieniem jest filtracja danych raportowych według określonego wzorca. Uwzględnia ona znaki specjalne *, ? określające wystąpienie odpowiednio dowolnego podciągu i pojedynczego znaku. By dokonać filtracji należy w polu edycyjnym w prawym górnym rogu okienka wpisać słowo, według którego nastąpi filtrowanie i wcisnąć guzik Filtruj. 

Za pomocą menu Widok -> Czcionka istnieje możliwość zmiany domyślnej czcionki listy prezentującej dane raportowe 




[Powrót do listy](/README.md)