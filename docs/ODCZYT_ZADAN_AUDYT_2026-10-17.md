# TSI — naprawa odczytu treści, 17 października 2026

Praca jest w toku. Wyniki regresji nie oznaczają rozumienia wszystkich zadań szkolnych.

## Wykonane poprawki

- Równania liniowe: zapis `2x`, mnożenie przez nawias, równanie sprzeczne i tożsamościowe. Sprawdzone również przez działające API.
- Nagłówek ćwiczenia, lista pytań i puste miejsca odpowiedzi nie blokują już odczytu pojedynczych pytań. Nierozpoznane warunki nadal są zgłaszane.
- Dziewięć pytań z ćwiczenia 3 „Koła i okręgi” otrzymuje komplet odpowiedzi. Sprawdzono przeciwny kierunek definicji i porównań.
- Długości złożone, np. `13 cm 2 mm`, oraz wartości pod nagłówkiem „o bokach podanej długości”. Przeliczanie jest dokładne, jednostki niezgodne są odrzucane.
- Pełne polecenia „Rozwiąż równanie…” i „Wykaż, że równanie… nie ma rozwiązań” trafiają do dokładnego solvera równań liniowych. Fałszywe twierdzenie o braku rozwiązań jest odrzucane z podaniem rozwiązania. Dodatkowe warunki nie są obcinane.

## Ten sam zestaw ZPE — 204 przypadki

Po poprawkach list i wymiarów: 17 odpowiedzi obliczeniowych, 3 odpowiedzi pojęciowe, 137 próśb o doprecyzowanie, 35 odmów zakresu i 12 przypadków wymagających danych. Wcześniej odpowiedź zwracano tylko w 6 przypadkach.

20 odpowiedzi nie oznacza 20 w pełni wykonanych ćwiczeń: część zawiera także polecenie narysowania figury, którego sam wynik liczbowy nie realizuje. Nie wszystkie odpowiedzi mają automatyczny niezależny wzorzec oceny. Pełne odpowiedzi zapisano w `structural-audit.json`; pierwotny wynik w sąsiednim katalogu `tsi_geometry_site_audit/audit-results.json`.

Przed dołączeniem pełnych poleceń z równaniami przeszły 842 testy regresji. Nowy czytnik poleceń równań przeszedł osobno 13 testów. Dashboard sprawdzono w przeglądarce: dziewięć odpowiedzi, długości złożone, widok mobilny, brak błędów JavaScript.

## Nowa próba egzaminacyjna i podręcznikowa

To próbka 10 zadań, nie komplet arkuszy ani wszystkich roczników. Wzorce odpowiedzi są przechowywane oddzielnie i nie są przekazywane do czytnika. Notację z PDF przepisano liniowo; zachowano liczby i warunki. Układ ułamków oraz wybrane strony sprawdzono na obrazie PDF. Automatyczne wydobycie tekstu PDF mieszało kolejność zadań i zapis ułamków, więc nie użyto go bez kontroli jako gotowego sprawdzianu.

Źródła:

- [CKE — gimnazjum 2019](https://egzaminy.gov.pl/cke/materialy-egzaminacyjne/egzamin-gimnazjalny?exam_session=2019), zadania 8 i 22.
- [CKE — matura maj 2025, formuła 2023](https://egzaminy.gov.pl/cke/materialy-egzaminacyjne/egzamin-maturalny?exam=egzamin-maturalny&exam_session=2025-maj&formula=F2023), zadania 9, 15, 25 i 31.
- [ZPE — Przed egzaminem: równania](https://zpe.gov.pl/a/przed-egzaminem---rownania/D1Hb4vfE2), ćwiczenia 11–14.

Pierwsze uruchomienie: 0 pełnych odpowiedzi na 10 zadań. Po poprawce pełnych poleceń: 2/10 — ćwiczenie 11 daje x=4, ćwiczenie 12 potwierdza brak rozwiązań. Pozostałe 8 nadal nie jest rozwiązane. Wynik i pełne wejścia: `exam-results.json`; powtarzalny sprawdzian: `exam_benchmark.py`.

Nadal wymagają pracy: procenty i bilans, układy z treści, ciągi z dodatkowymi warunkami, bryły i optymalizacja oraz zależności kątowe. Nie przypisano temu etapowi kompletnej obsługi matur, gimnazjum ani automatycznego uczenia się wszystkich zadań. Nie opublikowano nowego pakietu portable z tymi poprawkami.

## Dalsza naprawa: relacje procentowe i bilans

Włączono wspólną reprezentację niewiadomych, równań i ograniczeń dla porównania procentów jednej liczby, zmiany wypełnienia zbiornika i podziału budżetu dwóch zespołów. Po rozpoznaniu całego obsługiwanego polecenia solver rozwiązuje układ i sprawdza każdą relację przez podstawienie. Nie jest to nowo wytrenowany model językowy ani dowód rozumienia dowolnej treści.

Ten sam zestaw 10 zadań daje teraz 5 pełnych odpowiedzi: gimnazjum 2019 zadanie 8 — 64 l, matura 2025 zadanie 9 — 735000 zł dla zespołu A, ZPE ćwiczenia 11 — x=4, 12 — brak rozwiązań, 13 — x=40. Pozostałe 5 nadal nie jest rozwiązane. Pierwsze dwa wyniki sprawdzono także osobnym rachunkiem na ułamkach, bez wykorzystania równań zwróconych przez czytnik.

Przeszło 886 testów pełnej regresji. Następnie rozszerzono sprawdzanie wariantów odpowiedzi i tożsamości zbiornika; cały zestaw tej warstwy przeszedł 35 testów. Nie przedstawiamy 886 jako liczby ponownie uruchomionej po tych ostatnich czterech testach.

## Dokładny audyt wejścia i wyjścia czytnika oraz rdzenia

- Transport dashboardu: zadania długości 418 i 396 znaków dochodziły do parsera bez zmiany choćby jednego znaku. Odmowa wynikała z zakresu parsera. Formularz i główny opis mają limit 1000 znaków; niektóre czytniki dodatkowe — 512.
- Śledzenie rzeczywistych wywołań sześciu ścieżek: żadna nie wywoływała oryginalnego neuronowego `TSISystem.reply`. Starsze zadanie o dwóch liczbach wywoływało adapter matematyczny `manager_math.run_math_task`; adapter korzysta z SymPyBridge, co nie jest równoznaczne z wywołaniem neuronowego rdzenia. Nowe bilanse, jawne równania i relacje okręgu miały własne solvery/nauczycieli.
- Osobny test oryginalnego czytnika i rdzenia: 204 polecenia obejmujące 7 operatorów, trzy stany i dwie pary nazw. Poprawny odczyt operatora i argumentów: 156/204; poprawna końcowa odpowiedź: 187/204. Odpowiedź bywała poprawna przy błędnym odczycie. Ten sam rdzeń logiki, z poprawną strukturą na wejściu: 204/204; liczba obejmuje powtórzenie struktur dla dwóch form językowych.
- Rzeczywiście policzone unikalne parametry oryginalnego języka, pamięci i logiki: 784338. Osobny czytnik relacji okręgu ma 132501 parametrów, 21 klas i 46 form słownika treningowego; nie są to liczby opisujące całe TSI.
- Sprawdzono sumy kontrolne 11 plików oryginału z rejestru chronionych źródeł przed i po teście — bez zmian.
- Próba bezpośredniego podania 10 treści oryginalnemu interfejsowi ujawniła limit 160 znaków oraz nieobsługiwany znak stopnia. Krótsze zadania były mapowane na operator logiczny, bez równań.
- W odrębnym procesie eksperymentalnie zdjęto wyłącznie limit długości i zapisano znak stopnia jako słowo „stopni”. Wszystkie 10 treści przeszło, ale nadal nie powstał model matematyczny: interfejs zwracał operatory logiczne i wybrane fragmenty tekstu. Eksperyment był poza wyuczonym kontraktem i nie został wdrożony. Nie zmieniono plików źródłowych ani wag rdzenia.

Wniosek w granicach testu: występują zarówno ograniczenia techniczne wejścia, jak i niewystarczające lub brakujące odwzorowanie języka zadania na relacje matematyczne. Samo otwarcie przesyłu nie dodaje tego odwzorowania. Wyniki nie uzasadniają tezy, że rdzeń rozwiązuje dowolne zadania szkolne po usunięciu limitów.

Pełne lokalne ślady: `input-access-report.json`, `boundary-audit.json`, `neural-core-audit.json`, `core-transfer-audit.json` oraz `exam-results.json` w katalogu roboczym tego raportu. Dane referencyjne nie były przekazywane do czytników.
