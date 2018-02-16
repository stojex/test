# Tworzenie alarmów na wartościach raportowych
Wymagania:
- [ProcWin. Konfiguracja modułu](/ProcWin/ProcWin.-Konfiguracja-modułu.md) 
- [TODO: ProcWin. Definiowanie zmiennych]
- [TODO: ProcWin. Tworzenie procedur]
- [TODO: ProcWin. Operacje na wartościach raportowych]

Niejednokrotnie spotkasz się z problemem monitorowania wartości raportowej godzinowej lub dobowej. Klient wymaga prezentacji alarmu gdy wartość raportowa przekroczy określoną wartość.

Moduł AlSrv nie umożliwia bezpośredniej obserwacji wartości raportowej, a jedynie wartości bieżącej. Aby uzyskać wartość bieżącą posłużymy się modułem ProcWin. Przedstawię poniżej 2 warianty, które możesz wykorzystać. Zmienne w języku polskim pobierane są z modułu TelSrv. Nazwy w języku angielskim wykorzystywane są tylko w ramach procedury.

Pierwszy wariant przewiduje przepisanie wartości raportowej (ZMIENNA_GODZINOWA) do nowej zmiennej (ZMIENNA_BIEŻĄCA).
```
REMOTE ZMIENNA_GODZINOWA SERWER@ZMIENNA_GODZINOWA
REMOTE ZMIENNA_BIEŻĄCA SERWER@ZMIENNA_BIEŻĄCA

:BEGIN
CALL CurrentFromHour(ZMIENNA_GODZINOWA,ZMIENNA_BIEŻĄCA)
GOTO BEGIN

PROCEDURE CurrentFromHour(VARIABLE_HOUR,VARIABLE_CURRENT)
BEGIN
	GET VARIABLE_HOUR HREP TIME.YEAR TIME.MONTH TIME.DAY TIME.HOUR 0
	IF UNKNOWN VARIABLE_HOUR.HREP THEN
		SET_STATUS VARIABLE_CURRENT UNKNOWN
	ELSE
		:czekaj
		IF NOT READY VARIABLE_HOUR.HREP GOTO czekaj
		SET VARIABLE_CURRENT = VARIABLE_HOUR.HREP
	ENDIF
END
```
Drugi wariant przepisuje wartość raportową godzinową do wartości bieżącej tej samej zmiennej. Zmienna nie powinna mieć wykorzystywanej wartości bieżącej. Skrypt nie powinien być użyty dla zmiennej z dowolnym raportem wyliczanym z wartości archiwalnych.
```
REMOTE ZMIENNA SERWER@ZMIENNA

:BEGIN
CALL CurrentFromHour(ZMIENNA)
GOTO BEGIN

PROCEDURE CurrentFromHour(VARIABLE)
BEGIN
	GET VARIABLE HREP TIME.YEAR TIME.MONTH TIME.DAY TIME.HOUR 0
	IF UNKNOWN VARIABLE.HREP THEN
		SET_STATUS VARIABLE UNKNOWN
	ELSE
		:czekaj
		IF NOT READY VARIABLE.HREP GOTO czekaj
		SET VARIABLE = VARIABLE.HREP
	ENDIF
END
```
Przykłady pokazują monitorowanie wartości raportowej godzinowej. Jeśli potrzebujesz monitoringu wartości dobowej zamień wszystkie wystąpienia HREP na DREP.
Po tak uruchomionym skrypcie, możemy przygotować alarm dla zmiennych użytych w skrypcie (ZMIENNA_BIEŻĄCA lub ZMIENNA). Jeśli nie wiesz jak tworzyć i używać alarmów zajrzyj do artykułu: [TODO: Utworzyć taki artykuł]Tworzenie alarmów/zdarzeń.

[Powrót do listy](/README.md)