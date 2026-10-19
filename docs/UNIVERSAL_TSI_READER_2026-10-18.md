# Nowa warstwa TSI w math validatorze — 18 października 2026

Nowy czytnik ogólnej TSI jest aktywnym pierwszym etapem obsługi zadań tekstowych. Przeniesiono jego moduły, macierze odmiany i ról, słownik angielski, model wyboru działania oraz transformer odczytu kontekstu do lokalnego pakietu walidatora. Pakiet nie wymaga uruchomionego panelu ogólnej TSI. Zachowano licencje danych i kontrolę sum modeli.

Rdzeń H512 i jego wagi były już wspólne dla obu aplikacji: `TSI-NATIVE-H512-P2054186-9deec43d`. Nie wymieniono identycznych wag ani nie wykonano nowego treningu. Zmiana obejmuje warstwę wejściową, interpretację i połączenie z narzędziami.

## Co działa przez nowy czytnik

- Polecenia dodawania, odejmowania, mnożenia, dzielenia i obsługiwane plany dwuetapowe PL/EN.
- Jawne role liczb, kolejność działań, ujemne liczby i dokładne ułamki. Wybór uczonego modelu jest sprawdzany z kompletną strukturą polecenia przed obliczeniem.
- Negacja, alternatywa, brak argumentu, dodatkowy nierozpoznany warunek lub zerowy dzielnik zatrzymują wykonanie.
- Odczyt podanego źródła i pytania w kontrolowanym zakresie zdań o posiadaniu, łączników i warunków PL/EN. Odpowiedź zachowuje stan T/F/U i ślad audytu; U nie jest zamieniane na zaprzeczenie.

Wpisz w istniejącym polu zadania:

```text
Odejmij 3 od 10
```

Wynik: `7`. Po zmianie na `Od 3 odejmij 10`: `-7`.

```text
Multiply 3 by 4, then subtract 2
```

Wynik: `10`.

```text
Read: Anna has a telescope but John does not have a microscope.
Question: Does John have a microscope?
```

Odpowiedź: `No. John does not have a microscope.`

## Zachowane narzędzia i granice

Geometria, zadania o dwóch liczbach, optymalizacja, całki, macierze, audyt i wykresy zachowują swoje wyspecjalizowane narzędzia. Nowy moduł nie uznaje samej obecności słowa w słowniku za rozpoznanie matematycznej zależności. Nie oznacza to pełnego rozumienia dowolnego zadania ani automatycznej poprawy wszystkich rodzin geometrii. Dane jednostek i warunki nadal muszą być sprawdzone przez właściwy czytnik dziedzinowy.

Nowy czytnik działa w zwykłej ścieżce zadania; dotychczasowa opcja kontroli geometrii dotyczy dodatkowego sprawdzenia opisu geometrycznego. Solvery akademickie pozostają bez zmian. Zachowano wygląd istniejącego panelu, a w odpowiedziach nowego czytnika pokazano role liczb, wyrażenie i źródło.

## Weryfikacja

- Nowy adapter: 42/42.
- Zachowane narzędzia matematyczne: 245/245.
- Raporty i ich integralność: 22/22.
- Kontrola rzeczywistych odpowiedzi HTTP: 11 sprawdzeń, w tym odtworzenie raportu przez nowy czytnik, geometria i dwie liczby.
- Porównanie tych samych 22 specjalnie dobranych poleceń nowej funkcji: poprzednia ścieżka odpowiedziała na 0, nowa odpowiedziała poprawnie na 22. To wynik tego zestawu poleceń, a nie procentowa ocena całego walidatora.

Raporty obliczeń obejmują również pliki i modele nowego czytnika w identyfikacji wersji. Odtwarzanie wybiera tę samą ścieżkę odczytu; zmiana kodu lub danych zmienia identyfikator wersji raportu. Kopię poprzednich plików i manifest cofnięcia zachowano lokalnie w `backups/before-universal-reader-2026-10-18`.
