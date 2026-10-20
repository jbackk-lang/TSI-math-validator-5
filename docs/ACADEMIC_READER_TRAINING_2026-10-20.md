# Trening odczytu akademickiego — 20 października 2026

Przygotowano i zamrożono własny sprawdzian: 24 polecenia z pochodnych, całek nieoznaczonych i oznaczonych, równań, wyznaczników i macierzy odwrotnych, oraz 12 poleceń zanegowanych, niepełnych lub niejednoznacznych. To kontrolowane polecenia z jawnym wzorem po dwukropku, nie reprezentatywny przekrój wszystkich egzaminów akademickich.

## Co sprawdzono osobno

| Warstwa | Wynik |
|---|---:|
| Dotychczasowy czytnik: odczyt i wykonanie nowych poleceń | 0/24 |
| Narzędzia z poprawnie przekazanymi parametrami | 24/24 |
| Nowy uczony selektor + walidacja parametrów + narzędzia | 18/24 |
| Błędnie wykonane zadania z grupy 24 poprawnych poleceń | 0 |
| Wykonane polecenia z grupy 12 wymagających wstrzymania | 0/12 |
| Zachowanie wcześniejszych działań i odczytu źródła | 8/8 |
| Spójność odpowiedzi z odczytanym wzorem i wynikiem | 18/18 udzielonych odpowiedzi |

Ocena objaśnień była osobna: odpowiedzi podają zadanie, wzór, wynik i przy całce oznaczonej granice. Nie zawierają jeszcze pełnego objaśnienia metody krok po kroku. Spójność odpowiedzi nie jest oceną jakości nauczania ani dowodem swobodnego rozumienia opisu.

## Wykonany trening

Nowy moduł **TSI-ACADEMIC-INTENT-63ca677e**, **263 175 parametrów**, trenowano na **1680 przykładach**. Osobny DEV: **232 przykłady**, rozłączne całe polecenia; nie tylko podmiana liczb. Model wybiera pochodną, całkę nieoznaczoną, oznaczoną, równanie, wyznacznik, odwrotność lub wstrzymanie. Jawne dane matematyczne sprawdza osobny parser i solver.

Wybrano epokę 18 według straty na DEV. Trafność samych klas na DEV: 78,88%. Próg 0,75 wybrano na DEV po uwzględnieniu kompletności danych i warunków wykonania; na DEV 102 poprawne przyjęcia, bez błędnie wykonanych zadań i bez wykonania odrzuconych poleceń. Odróżniamy klasyfikację sieci od poprawności całego kontrolowanego przepływu.

Próg wdrożenia ustalony przed sprawdzianem: co najmniej **22/24** kompletnych poprawnych odpowiedzi, brak niebezpiecznych wykonań i zachowanie wcześniejszych prób. Dodatkowo wymagano braku błędnych wykonań w grupie poprawnych poleceń. Wynik **18/24** nie spełnia progu: **modułu nie włączono do panelu i nie zastąpiono aktywnego czytnika**. Wagi H512 pozostają bez zmian.

## Nierozpoznane sformułowania

Sześć przypadków wstrzymano. Przykłady: „Jak wygląda pochodna tego wyrażenia”, „Odtwórz funkcję z jej pochodnej”, „Dla jakich x zachodzi równość”, „Wyznacz argumenty zerujące wyrażenie”, „Wyznacz wartość det A”, „Podaj A do potęgi minus jeden”. Pokazuje to luki w rozumieniu celu i parafraz, a nie błąd obliczenia tych zadań przez solver.

Zachowano wyniki negatywne. Po ocenie nie dostrajano modelu ani progu do tego sprawdzianu. Zbiór treningowy, DEV, zamrożony sprawdzian, wagi, rzeczywiste odpowiedzi i protokół są w lokalnym archiwum treningu. Publicznie udostępniamy wyłącznie dokumentację.

## Dalszy kierunek

Rozszerzyć dane uczące o znaczenie operacji oraz odwrócone relacje, np. pochodna a odtwarzanie pierwotnej. Osobno rozwijać objaśnienia oparte na sprawdzonych krokach narzędzi. Kolejna wersja wymaga nowego niezależnego sprawdzianu; ten zestaw nie może udawać ponownie nieznanego testu po wykorzystaniu informacji o jego błędach.
