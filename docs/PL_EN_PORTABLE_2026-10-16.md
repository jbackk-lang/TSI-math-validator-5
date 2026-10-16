# PL/EN i wersja portable — 16.10.2026

## Interfejs PL/EN

Wspólny przełącznik PL/EN na wszystkich ekranach. Tłumaczy menu, pola, opisy, komunikaty błędów i dynamiczne wyniki (w tym audyt i kontrprzykłady). Wybór zapisuje się lokalnie w przeglądarce; przejście między zadaniami i odświeżenie go zachowuje. Zmiana języka nie modyfikuje wpisanych wyrażeń, macierzy ani kroków. Matematyczne i techniczne zapisy wyników pozostają niezmienione.

**To tłumaczenie interfejsu, nie nowy parser angielskich poleceń.** Polecenia menedżera i kontrolowane opisy zadań tekstowych nadal wymagają polskiego języka. Oba ekrany pokazują taką informację po polsku lub angielsku. Wzory, macierze, wybór stanów logicznych i równania audytu mogą być używane z angielskim interfejsem bez polskiego opisu. Raporty JSON zachowują kanoniczne dane narzędzia.

Tłumaczenia są w lokalnym katalogu; tekst użytkownika nie jest wysyłany do usług tłumaczących. Sprawdzono przełączanie w obie strony, zachowanie wpisu, odświeżenie i nawigację, angielskie komunikaty o błędach, wyniki audytu i widok mobilny.

## Portable z kodem

Lokalna paczka Windows x64 zawiera pełny kod aplikacji, modele, dokumentację oraz osobnego Pythona 3.12 i biblioteki. Nie wymaga instalowania Pythona ani pobierania modeli przy starcie. Pakietu z kodem i wagami nie publikuje się w dokumentacyjnym repozytorium GitHub.

Po rozpakowaniu całego katalogu do zapisywalnego miejsca uruchamia się `START.bat`. `ZATRZYMAJ.bat` zatrzymuje wyłącznie własną rozpoznaną instancję portable. Serwer działa na 127.0.0.1 i wybiera wolny port od 8797, osobny od zwykłego dashboardu i MUZ. Przenosi się cały katalog, nie sam plik python.exe.

Kod znajduje się w `app/code`, interfejs w `app/dashboard`, własne środowisko w `python`. Dane wykonania są tworzone w `app/runtime`. Nie dołączono historii `.git`, prywatnych dzienników starego runtime ani środowisk deweloperskich. Źródła historycznych eksperymentów są zachowane, ale nie wszystkie stanowią gotowe polecenia portable.

Usunięto zależność aktywnego rdzenia od zapisanych dawnych absolutnych ścieżek modeli: lokalny plik jest wybierany wyłącznie po potwierdzeniu oczekiwanej sumy SHA-256. Wagi i chronione konfiguracje pozostają bez zmian. Poprawkę obejmują testy przeniesienia, odrzucenia zmienionego modelu i blokady wyjścia poza katalog artefaktów.


## Wynik weryfikacji

**326/326** testów dotychczasowej matematyki, narzędzi, diagnostyki i audytu oraz **3/3** testy bezpiecznego odnajdywania przeniesionych modeli. Kontrole przeglądarkowe PL/EN zaliczone w zwykłej instalacji i przeniesionym portable: menu i wyniki dynamiczne, błędy, powrót do PL bez utraty wpisu, zapis preferencji, nawigacja i układ mobilny.

Portable uruchomiono w nowym katalogu ze spacją w nazwie, używając wyłącznie dołączonego Pythona. Offline sprawdzono całkę, odwrotność macierzy, audyt utraty x=0 i wyuczony menedżer: x²−9 → −3,3. Proces testowy blokował odczyt starych katalogów aplikacji; biblioteka standardowa i zależności pochodziły z paczki. Test nie zastępuje próby na innym fizycznym komputerze.

Sprawdzono ponowne uruchomienie bez tworzenia drugiej instancji i zatrzymanie przez własny token. Zwykły dashboard 8795 i MUZ 8796 pozostały dostępne. Limit wywołania narzędzi akademickich w portable wynosi 90 sekund, aby uwzględnić pierwszy import bibliotek; zwykła instalacja zachowuje 15 sekund. Pierwszy start modeli może trwać dłużej. 11 chronionych plików i aktywny model bez zmiany wag.
