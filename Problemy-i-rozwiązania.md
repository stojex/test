# TelWin SCADA - najczęściej występujące problemy
## Spis treści:
> - [Błąd uruchomienia pomocy](Problemy-i-rozwiązania.md#b%C5%82%C4%85d-uruchomienia-pomocy) 
> - [Plik pomocy uruchamia się ale jest pusty](Problemy-i-rozwiązania.md#plik-pomocy-uruchamia-si%C4%99-ale-jest-pusty)
> - [Link 3](Problemy-i-rozwiązania.md#)

## Błąd uruchomienia pomocy
Część modułów systemu TelWin SCADA np. AlSrv i TelSrv posiadają swoją dokumentację w formie plików pomocy systemu Windows. Gdy korzystamy z modułu możemy wcisnąć przycisk F1, który powinien uruchomić te pliki. Jeśli wciśnięcie F1 kończy się komunikatem: "Błąd uruchomienia pomocy" to należy do katalogu Exe wrzucić pliki *.chm, które udostępniane są w archiwum np. **TelWinSCADA_6_07_help.zip**.

![Okno raportu](/img/Problemy-i-rozwiazania-blad-uruchomienia-pomocy.png)

## Plik pomocy uruchamia się ale jest pusty
Aby móc przeglądać pliki chm z zasobu zdalnego należy usunąć restrykcje systemu zabezpieczającą przed tym procederem - ustawienie domyślne. W tym celu należy ustawić klucz w rejestrze systemu:
```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\HTMLHelp\1.x\ItssRestrictions] 
"MaxAllowedZone"=dword:00000004 
```


[Powrót do listy](/README.md)