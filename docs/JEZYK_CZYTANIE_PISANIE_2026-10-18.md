# Czytanie i pisanie TSI — stan 18.10.2026

To oddzielny eksperyment językowy, zachowany lokalnie razem z kodem, wagami i wynikami. Dashboard matematyczny nie korzysta jeszcze z nowych modeli. Nie zastąpiono pierwotnego rdzenia TSI.

## Co działa w potwierdzonym zakresie

Nadrzędny kontroler wybiera kontrolowaną analizę zdania. Dla poleceń dotyczących dna i pokrywki sprawdza części mowy, odmianę, szyk, negację i kompletność ról. Osobna gałąź rozpoznaje wybrane zdania o promieniu, wysokości, boku, masie, prędkości, objętości, czasie i polu.

Są cztery rodzaje wypowiedzi: podanie wartości, zaprzeczenie wartości, pytanie i wskazanie brakującej wartości. Dla każdego są dwa sposoby sformułowania. Jednostka musi pasować do wielkości; przeliczanie jednostek nie jest częścią tego eksperymentu.

Generator GRU uczy się budowy zdania. W najbezpieczniejszym wariancie nazwy w odpowiednim przypadku, liczby i jednostki są wstawiane z jawnych pól. Następnie cały tekst jest ponownie analizowany i porównywany ze znaczeniem wejściowym. Wypowiedź zmieniająca sens jest odrzucana. To podejście hybrydowe: część uczona oraz jawna matryca form i danych.

Przykłady rzeczywistego działania kontrolera:

| Wejście / dane | Zachowanie |
|---|---|
| „Ile wynosi wysokość w cm?” bez danych | „Brakuje wysokości. Podaj wysokość w cm.” |
| „Ile wynosi promień w cm?” i jawna dana 123.456789012 cm | „Promień wynosi 123.456789012 cm.” |
| „Promień nie wynosi 3 cm.” | Zachowuje zaprzeczenie, zamiast zamieniać je w twierdzenie |
| „Dna i pokrywki nie pomijaj.” | Rozpoznaje uwzględnienie obu części |
| „Promień wynosi 3 cm albo 7 cm.” | Prosi o doprecyzowanie; nie usuwa alternatywy |

Dane do odpowiedzi podaje się jawnie. Kontroler nie zgaduje wartości, nie modyfikuje wag podczas dialogu i nie zapisuje automatycznie faktów. Nie wykonuje obliczeń w aktywnym solverze.

## Wyniki i nieudane próby

| Próba | Wynik i znaczenie |
|---|---|
| Mały pierwszy generator poleceń, 12 548 parametrów | 52/52 trening, 12/12 odłożonych kombinacji; tylko dno/pokrywka, odmiana, negacja, szyk |
| Pierwszy wspólny czytnik i generator, 66 472 parametry | 57/57 odczyt, 45/57 pisanie na odłożonych kombinacjach; zmieniał jednostki |
| Stałe przekazywanie struktury przy każdym kroku, 86 059 parametrów | Trzy starty: pisanie 94/95, 95/95, 94/95; odczyt 95/95, 94/95, 95/95. To ten sam test powtórzony trzy razy |
| Kopiowanie liczb i jednostek, ale uczenie nazw, 33 554 parametry | 4/13 w odłożonym teście; nie opanował przenoszenia wszystkich nazw w małym zbiorze |
| Oddzielna matryca nazw/odmiany i uczona konstrukcja, 32 308 parametrów | Trzy starty: 13/13 na wiązaniu pól. Wspólne schematy zdań występują w treningu i teście; nie jest to test nieznanej gramatyki |
| Próba zachowania danych | 768 różnych kombinacji wielkości, zgodnych jednostek, rodzaju zdania, stylu i liczb; 768/768 dla każdego z trzech modeli. Trzech powtórzeń nie liczymy jako 2304 niezależnych zadań językowych |

W ostatnim teście są zero, ułamki dziesiętne i długie liczby. Poprawiono błąd normalizacji, który mógł zaokrąglać liczbę przekraczającą domyślną precyzję obliczeń dziesiętnych. Teraz kanonizacja usuwa wyłącznie zbędne zera, bez zaokrąglania.

Pamięć leksykalna to 67 pojęć, 310 form i 13 cech. Jej kwantyzacja zachowuje reprezentację w tym zakresie; nie oznacza nauczenia całego słownika. Nadrzędna macierz gramatyczna korzysta z małego ręcznie opisanego zasobu wszystkich dziesięciu części mowy. Nie jest to pełna gramatyka polska.

## Jak odtworzyć lokalnie

W katalogu z pełnym kodem:

```text
python code/manager/language_communication.py "Ile wynosi wysokość w cm?"
python code/manager/quantity_communication.py --seed 17 --out code/manager/quantity_experiment_v2/seed17
python code/manager/slot_copy_language.py --seed 17 --out code/manager/slot_copy_experiment_v2/seed17
python code/manager/language_communication_experiment/evaluate-copy-numbers.py
```

Ponowny trening pod wskazanym katalogiem zastępuje jego checkpoint i raport; do osobnego porównania należy podać inny katalog wyjściowy. Wyniki pierwszych nieudanych wersji są zachowane w osobnych katalogach. Plik `language_communication_experiment/checksums.json` identyfikuje zapisane moduły, dane i checkpointy. Dane syntetyczne i wagi pozostają lokalne.

## Ograniczenia i następny krok

To kontrolowane schematy, nie swobodna rozmowa ani rozumienie dowolnego zadania. Nowe konstrukcje, dodatkowe warunki i niezgodne jednostki powodują odmowę interpretacji. Odczyt ilościowy jest obecnie regułowy w kontrolerze; osobno wytrenowany czytnik neuronalny ma zapisane wyniki, ale nie zastępuje tego zabezpieczenia. Sukces kopiowania pól nie dowodzi rozumienia nowego słownictwa.

„Mówienie” oznacza tutaj formułowanie tekstu wypowiedzi. Nie ma jeszcze syntezy głosu ani rozpoznawania mowy.

Następny etap: zamrozić niezależny zestaw nowych konstrukcji wielozdaniowych, relacji dwóch wielkości i naturalnych pytań; zachować pierwszy wynik; rozbudować odczyt ról i sprawdzić cały przepływ z solverem przed włączeniem do dashboardu. Nie podłączać arbitralnie nowych cech do przestrzeni pierwotnego rdzenia.

## Weryfikacja kodu

Łącznie przeszło 1900 różnych testów regresji: 1574 w podkatalogu testowym i 326 pozostałych testów menedżera. Cztery starsze testy początkowo uruchomiono bez wymaganej zmiennej lokalizacji adaptera; po jej ustawieniu 4/4 przeszły. Dodano przenoślną konfigurację testową, która wyznacza adapter względem repo i respektuje jawne ustawienie użytkownika. Końcowy zapis zdań i dokładność danych zweryfikowano również zestawem 229/229; to powtórzone testy, nie dodatkowe niezależne zadania.

Pełna regresja lokalnie: `python -m pytest code/manager -q`.


## Pojemność i zapominanie — porównanie 18.10.2026

Zastosowano te same dane i podziały w trzech startach (17, 29, 43). Zwiększono szerokość GRU z 80 do 192, czyli pojemność z **52 628 do 253 668 parametrów**. Pozostałe ustawienia uczenia zachowano. W każdej szerokości najpierw uczono starych poleceń, a następnie porównano naukę samych nowych zdań z nauką zawierającą także wcześniejsze ćwiczenia.

| Model | Stare przed nową nauką | Stare po nauce bez powtórek | Stare po nauce z powtórkami | Nowe po nauce z powtórkami |
|---|---|---|---|---|
| 52 628 parametrów, trzy starty | 11/12, 11/12, 12/12 | 0/12 w każdym | 11/12 w każdym | 13/13 w każdym |
| 253 668 parametrów, trzy starty | 12/12 w każdym | 0/12 w każdym | 12/12 w każdym | 13/13 w każdym |

Wynik dotyczy **zachowania znaczenia**. Dokładne brzmienie jest raportowane oddzielnie: większy model z powtórkami uzyskał 11/12, 12/12, 12/12 identycznych starych zdań oraz 13/13 identycznych nowych. Inna poprawna wypowiedź o tym samym sensie nie jest liczona jako identyczny tekst.

W tym małym doświadczeniu większy model z powtórkami radzi sobie najlepiej. Sama pojemność nie zapobiegła zapominaniu. Powtórki wykorzystują dodatkowe stare przykłady, więc nie jest to porównanie przy identycznym koszcie obliczeń. Testy były powtarzane i znane z wcześniejszej analizy; nie stanowią nowego niezależnego egzaminu językowego. Nie zmodyfikowano oryginalnych wag TSI i nie przełączono dashboardu na model eksperymentalny.

Wagi trzech etapów (`before.pt`, `new_only.pt`, `replay.pt`), dane i pełne raporty są lokalnie w `code/manager/rehearsal_experiment/` oraz `code/manager/rehearsal_capacity192/`. Zestawienie i protokół: `code/manager/language_communication_experiment/capacity_results.json` oraz `capacity_protocol.json`.

Odtworzenie większego modelu: `python code/manager/language_rehearsal.py --seed 17 --hidden 192 --out code/manager/rehearsal_capacity192/seed17`.

Kolejny konieczny sprawdzian: nowe niezależne konstrukcje zdań, większy słownik oraz utrzymanie umiejętności po kilku kolejnych tematach.
