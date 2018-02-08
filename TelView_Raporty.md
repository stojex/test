# TelView - wbudowane raporty
Raporty umożliwiają sprawne tworzenie zestawów danych raportowych, prezentowanych w formie tabularycznej. Na raporcie tym mogą być prezentowane dane bieżące, archiwalne, raportowe: godzinowe, dobowe, miesięczne i okresowe.

## Tworzenie raportu
Przygotowanie raportu sprowadza się do sparametryzowania opcji i listy zmiennych, które będą prezentowane w trybie prezentacji danych. Okno edycyjne raportu prezentuje się następująco:
![Okno raportu](https://github.com/stojex/test/blob/master/img/TelView_Raporty_Okno_Edycji.png)

Przejdziemy teraz po wszystkich elementach okna edycji i zobaczymy jak te opcje wpływają na wygląd naszego raportu.

### Tytuł
Parametr Tytuł pozwala na zdefiniowanie tytułu okna, który zostanie wyświetlony w trybie prezentacji danych

![Tytuł okna raportu](https://github.com/stojex/test/blob/master/img/TelView_Raporty_Okno_Edycji_Tytuł_Okna.png)

#### Typ danych
Parametr Typ danych określa rodzaj prezentowanych danych (bieżące, archiwalne, godzinowe, dobowe, miesięczne, okresowe). Dla wartości archiwanych należy dodatkowo zdefiniować w polu Okres archiwizacji czas (w minutach).

![Tytuł okna raportu](https://github.com/stojex/test/blob/master/img/TelView_Raporty_Okno_Edycji_Typ_Danych_bieżące.png)
![Tytuł okna raportu](https://github.com/stojex/test/blob/master/img/TelView_Raporty_Okno_Edycji_Typ_Danych_archiwalne.png)
![Tytuł okna raportu](https://github.com/stojex/test/blob/master/img/TelView_Raporty_Okno_Edycji_Typ_Danych_raportowe.png)

#### Dowolny zakres danych

Parametr Dowolny zakres danych definiuje zakres prezentowania danych w trybie prezentacji. Zaznaczenie opcji spowoduje w trybie prezentacji wyświetlenie dwóch pól umożliwiających wybranie początku i końca okresu. W przeciwnym razie dane będą prezentowane w domyślnym zakresie. Dla danych godzinowych będzie to doba, dla dobowych i okresowych – miesiąc, a dla danych miesięcznych – rok.



#### Godzina bazowa

Parametr Godzina bazowa pozwala na zdefiniowanie początkowej godziny doby. Opcja ta będzie dostępna wyłącznie dla danych raportowych godzinowych i przy wyłączonej opcji Dowolny zakres danych.



#### Poziom uprawnień lub grupa użytkowników

Parametr Poziom uprawnień lub grupa użytkowników pozwala na ograniczenie dostępu do raportu, dla użytkowników mających niewystarczający poziom uprawnień lub nie należących do podanej grupy lokalnej. Raport będzie dostępny tylko dla użytkowników posiadających poziom uprawnień równy lub wyższy od wymaganego dla danego raportu. Wprowadzenie poziomu uprawnień 0 spowoduje udostępnienie danego raportu wszystkim użytkownikom.



### Dostępne zmienne

Grupa parametrów Dostępne zmienne pozwala na wyświetlenie drzewa zmiennych dla wybranego Źródła. Włączenie parametru Filtr uaktywni dwa pola edycyjne Nazwa i Opis umożliwiające wprowadzenie wzorców filtrowania prezentowanego drzewa zmiennych. Wzorzec może zawierać znak „*” symbolizujący wystąpienie dowolnego ciągu znaków (także pustego) lub znak „?” symbolizujący wystąpienie jednego znaku. Zaznaczenie zmiennej, a następnie naciśnięcie przycisku Dodaj spowoduje przeniesienie zmiennej do grupy parametrów Wybrane zmienne (zmienna może zostać dodana do listy wielokrotnie). Istnieje również łatwiejszy sposób dodawania zmiennych poprzez ich zaznaczenie a następnie przeciągnięcie (drag & drop) za lub przed odpowiedni wiersz danych w tabelce Wybrane zmienne.



### Wybrane zmienne

Grupa parametrów Wybrane zmienne pozwala na modyfikację parametrów listy zmiennych, które będą wyświetlane w trybie prezentacji danych. Dla każdej zmiennej istnieje możliwość zmiany Nazwy pełnej, Mnożnika, Formatu, Funkcji i Czcionki eksportu poprzez zaznaczenie lewym przyciskiem myszy wybranego pola. Zaznaczenie jednej lub wielu linii na liście, a następnie naciśnięcie przycisku Usuń na okienku lub Delete na klawiaturze spowoduje usunięcie zaznaczonych zmiennych z listy. Położenie grupy lub pojedynczych zmiennych można zmieniać albo przez użycie przycisków W górę i W dół albo za pomocą skrótu klawiszowego: prawy ALT + strzałka w górę / w dół. Zaznaczenie wszystkich wierszy tabelki odbywa się za pomocą skrótu CTRL + A. Zaznaczenie wielu pojedynczych elementów na liście, a następnie naciśnięcie przycisku Grupuj/Rozgrupuj spowoduje utworzenie z tych zmiennych grupy z unikalnym identyfikatorem. Zdefiniowanie Nazwy pełnej dla grupy umożliwi prezentację w trybie uruchomieniowym raportu nazwy zamiast identyfikatora. Zaznaczenie elementu grupowego i naciśnięcie przycisku Grupuj/Rozgrupuj spowoduje rozgrupowanie elementów należących do grupy. Funkcjonalność zawarta pod przyciskiem Aktualizuj dane, zapewnia wypełnienie pól Nazwa pełna oraz Opis aktualnymi danymi z serwera. Należy w tym miejscu wspomnieć o sytuacji szczególnej; pole "Nazwa pełna" zmiennej nie jest aktualizowana jeżeli jest pusta po stronie serwera.



Kolumny tworzące listę wybranych zmiennych:

Parametr Nazwa pełna może być automatycznie wypełniany w trybie uruchomieniowym raportu:
nazwą pełną z definicji zmiennej, jeśli w polu zostanie wpisany znak tyldy ‘~’
zdefiniowanym tekstem, w którym możemy korzystać z następujących parametrów:

- %NAME% - uzupełniany nazwą zmiennej,
- %SRC% - uzupełniany źródłem zmiennej,
- %DESC% - uzupełniany opisem zmiennej.

Wartość w kolumnie Mnożnik będzie brana pod uwagę w trybie uruchomieniowym na dwa sposoby. Pierwszy z nich dotyczy przemnożenia otrzymanych wartości ze źródła danych przez bezwzględną wartość mnożnika (nie będzie brany pod uwagę znak ‘-‘ przed wartością mnożnika). Drugi sposób dotyczy wyliczenia wartości grupy. Znak ‘-‘ będzie decydował, czy wartość elementu zostanie dodana do grupy, czy też odjęta od niej.
Kolumna Format pozwala na zdefiniowanie formatu wyświetlania wartości w trybie uruchomieniowym. Zasada jest identyczna jak w przypadku elementu Pomiar. Wartość 10 oznaczać będzie, że liczba będzie wyświetlona przez maksymalnie dziesięć cyfr. Wartość 8.2 oznaczać, będzie liczbę składającą się z pięciu cyfr i dwóch po przecinku (jeden znak zostanie wykorzystany jako separator liczby).
Kolumna Czcionka eksportu pozwala na wybranie czcionki, która zostanie wykorzystana podczas eksportu prezentowanych wartości do arkusza kalkulacyjnego Microsoft Excel.


### Parametry prezentacji listy wybranych zmiennych

#### Podsumowanie

Parametr Podsumowanie umożliwia wybranie jednej z funkcji podsumowujących dane w trybie prezentacji.

#### Format etykiety czasowej

Parametr Format etykiety czasowej kolumn pozwala na zmianę domyślnego formatu etykiety czasowej kolumn wyświetlających dane (%d-%m-%Y |%H:%M). Pionowa kreska oznacza podział etykiety i wyświetlenie jej w dwóch liniach.

#### Ukrywanie statusu wartości

Parametr Ukrywanie statusu wartości umożliwia włączenie/wyłączenie wyświetlania statusów wartości.

#### Automatyczne potwierdzanie wprowadzonych danych

Parametr Automatyczne potwierdzanie wprowadzonych danych umożliwia włączenie/wyłączenie automatycznego potwierdzania zmienionych wartości.

#### Transpozycja tabeli

Parametr Transpozycja tabeli umożliwia włączenie/wyłączenie transpozycji (zamianę wierszy i kolumn) prezentowanych danych raportowych.

#### Ukrywanie kolumny z opisem

Parametr Ukrywanie kolumny z opisem umożliwia ukrycie tej kolumny w trybie prezentacji.

#### Ignorowanie wartości nieznanych

Parametr Ignorowanie wartości nieznanych spowoduje ignorowanie nieznanych wartości podczas liczenia wartości określonych przez funkcje.

#### Odwrócenie osi czasu

Parametr Odwrócenie osi czasu umożliwia wyświetlenie danych w odwróconej kolejności względem czasu (od najpóźniejszych do najwcześniejszych).

#### Ukrywanie wierszy z wartościami nieznanymi

Parametr Ukrywanie wierszy z wartościami nieznanymi umożliwia włączenie/wyłączenie wyświetlenia danych bez wierszy, które w całości składają się z wartości nieznanych.

#### Wyróżnianie braku kompletności wartości raportowej

Parametr Wyróżnianie braku kompletności wartości raportowej umożliwia włączenie/wyłączenie wyświetlenia braku kompletności wartości raportowej, w postaci zmiany koloru tekstu dla wartości niekompletnej.

#### Kontrola danych raportowych

Grupa parametrów Kontrola danych raportowych pozwala na zdefiniowanie Dopuszczalnej różnicy (wyrażonej w procentach), o którą mogą różnić się dwie sąsiednie wartości raportowe. W przypadku przekroczenia różnicy wartość zostanie wyróżniona Kolorem po przekroczeniu. Zaznaczenie opcji Automatyczna kontrola spowoduje sprawdzenie raportu po każdorazowej zmianie parametru Dopuszczalna różnica w trybie prezentacji danych lub aktualizacji raportu.



UWAGA!!!

Zaznaczenie wiersza na liście wybranych zmiennych, a następnie dodanie lub wstawienie nowej zmiennej z listy dostępnych zmiennych, spowoduje dodanie nowej zmiennej z parametrami zmiennej zaznaczonej.




You can use one `#` all the way up to `######` six for different heading sizes.

If you'd like to quote someone, use the > character before the line:

> Coffee. The finest organic suspension ever devised... I beat the Borg with it.
> - Captain Janeway

There are many different ways to style code with GitHub's markdown. If you have inline code blocks, wrap them in backticks: `var example = true`.  If you've got a longer block of code, you can indent with four spaces:

    if (isAwesome){
      return true
    }

GitHub also supports something called code fencing, which allows for multiple lines without indentation:

```
if (isAwesome){
  return true
}
```

And if you'd like to use syntax highlighting, include the language:

```javascript
if (isAwesome){
  return true
}
```


GitHub supports many extras in Markdown that help you reference and link to people. If you ever want to direct a comment at someone, you can prefix their name with an @ symbol: Hey @kneath — love your sweater!

But I have to admit, tasks lists are my favorite:

- [x] This is a complete item
- [ ] This is an incomplete item

When you include a task list in the first comment of an Issue, you will see a helpful progress bar in your list of issues. It works in Pull Requests, too!

And, of course emoji! :sparkles: :camel: :boom:
