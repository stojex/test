# Struktura katalogów w systemie TelWin SCADA
Domyślnie program instalacyjny umieszcza system TelWin SCADA® w katalogu C:\<Program Files>\Tel-Ster\TelWinX. Poniżej zaprezentuje jednak proponowaną strukturę katalogów, która ułatwia zarządzanie i administrację aplikacją. Podstawowy katalog to np. **C:\TelWin** (może być dowolny inny), a w nim następujące 4 katalogi:
- App (katalog aplikacji systemu TelWin):
  - App\Al – katalog dla list alarmów modułu TelView 
  - App\Lib – katalog dla biblioteki elementów modułu TelView 
  - App\Pic – katalog dla plików graficznych modułu TelView 
  - App\Proc – katalog dla procedur modułu ProcWin 
  - App\Rep – katalog dla raportów modułu TelView 
  - App\Sh – katalog dla schematów wizualizacyjnych modułu TelView 
  - App\Wav – katalog dla plików dźwiękowych modułu TelView 
  - App\Var – katalog dla plików baz zmiennych modułów np. AlSrv, TelSrv 
- Data (katalog dla danych systemu TelWin):
  - Data\Archive – katalog dla danych archiwalnych
  - Data\DayRep – katalog dla danych raportowych dobowych 
  - Data\HourRep – katalog dla danych raportowych godzinowych 
  - Data\MonthRep – katalog dla danych raportowych miesięcznych 
  - Data\SpanRep – katalog dla danych raportowych okresowych 
- Exe (pliki wykonywalne systemu TelWin)
- Logs (katalog dla plików rejestracji systemu TelWin)

Aby móc tworzyć pliki rejestracji w tym katalogu Logs należy w pliku TelWin.ini ustawić ścieżki dla wpisów Logi lokalnie i Logi sieciowo jak zaprezentowano poniżej: 
```
[Katalogi]
Logi lokalnie=@..\Logs
Logi sieciowo=@..\Logs
```

W katalogu Exe umieszczane są pliki zawierające kod wykonywalny poszczególnych modułów systemu. W przypadku aktualizowania systemu bez korzystania z wersji instalacyjnej, rozpakowaną zawartość odpowiedniego pliku aktualizacji (np. TelWinSCADA_x64_6_06_13_release.zip) należy umieścić w tym katalogu (dla uniknięcia pomyłek zaleca się uprzednie usunięcie aktualizowanych plików). 

W katalogu App umieszczane są pliki konfiguracyjne poszczególnych modułów (rozszerzenia plików m. in. ini, var, cnf), plik z bazą użytkowników (rozszerzenie pliku dta), kopie zapasowe plików konfiguracyjnych i inne pliki niezbędne do pracy systemu TelWin SCADA®. 

Część danych poszczególnych modułów jest zapisywana w podkatalogach katalogu App (schematy synoptyczne modułu TelView czy procedury modułu ProcWin). Lokalizacja tych danych może być dowolnie modyfikowana przez administratora systemu TelWin SCADA® przez odpowiednie zapisy w dialogach konfiguracyjnych lub plikach ini odpowiednich modułów. 

