# Diagnoza odczytu zadań ZPE — 17.10.2026

Przejrzano 204 zapisane przypadki z pięciu materiałów ZPE: koła i okręgi, obwody prostokątów i kwadratów, trójkąty (dwa materiały) oraz wielokąty. Zestaw obejmuje 129 numerowanych ćwiczeń, ich warianty i wyodrębnione pytania. Nie jest to 204 niezależnych zadań rozwiązywalnych wyłącznie z tekstu.

## Korekta wcześniejszego wyniku

Wcześniejsze **20/204** oznaczało zwrócenie odpowiedzi, nie potwierdzenie pełnego wykonania. Po sprawdzeniu treści:

- **15 kompletnych odpowiedzi**: 12 obwodów sprawdzonych niezależnym rachunkiem ułamkowym i przeliczeniem jednostek oraz trzy odpowiedzi dotyczące własności figur.
- **4 częściowe wykonania**: poprawne obliczenie, ale niewykonany rysunek wymagany poleceniem.
- **1 błędna interpretacja tabeli**, teraz zablokowana: niezależne wartości z kolejnych wierszy zostały wcześniej dodane jak jedna długość złożona.
- Łącznie po poprawce **185 przypadków pozostaje bez kompletnego rozwiązania**, obok 15 kompletnych i czterech częściowych.

Wynik nie dowodzi uniwersalnego rozumienia geometrii ani wszystkich ćwiczeń na stronach.

## Przyczyny według zapisanego wejścia

| Główna kategoria | Przypadki |
|---|---:|
| Relacje możliwe do rozpatrywania z tekstu | 132 |
| Konstrukcja, rysowanie lub manipulacja | 34 |
| Format źródła: tabela, warianty, zbyt długi tekst | 22 |
| Brakujące dane z ilustracji | 9 |
| Dowód lub uzasadnienie | 5 |
| Brak danych liczbowych | 1 |
| Pomiar | 1 |

Każdy przypadek ma jedną główną kategorię; wymagania mogą się nakładać. Klasyfikacja opisuje zapisane wejście, nie wszystkie elementy widoczne na ZPE. Długie wejścia przekraczające limit 1000 znaków wymagają osobnej obsługi formatu. To nie jest dowód braku wiedzy matematycznej. Nie wykryto przenikania innych ćwiczeń przez ekstraktor; część źródeł zawiera równolegle kilka wariantów tego samego ćwiczenia.

## Następny zakres

Wśród nierozwiązanych zadań tekstowych: własności figur i kwantyfikatory — **54**, kąty — **33**, długości/obwody/proporcje — **18**, pola/wymiary — **11**, inne definicje — **1**.

Wybrano własności figur oraz znaczenie „każdy”, „może”, „musi”, „nie może”. To 54 przypadki z **18 ćwiczeń źródłowych**, 37 sformułowań po usunięciu oczywistych powtórzeń nagłówka i „Czy”. Nie oznacza to 37 różnych problemów matematycznych.

Przed rozbudową zamrożono osobny zestaw **30 nowych sformułowań**. Punkt odniesienia: **2/30 poprawnych odpowiedzi, zero błędnych zaakceptowanych odpowiedzi**, pozostałe nierozstrzygnięte. Osobne **6/6 kontroli brakujących danych** prawidłowo zatrzymano. Odpowiedzi wzorcowe nie są przekazywane czytnikowi, a zestaw nie trafia do banku nauki użytkownika. Po użyciu do napraw będzie to zestaw akceptacyjny; końcowa ocena wymaga kolejnego niezależnego zestawu.

Ten etap przygotowuje rozbudowę. Nie wdrożono jeszcze nowego rozumowania o wszystkich własnościach figur ani treningu, który rozwiązuje te 54 przypadki.

## Wdrożone poprawki i sprawdzenie

Czytnik nie łączy długości przez granicę wiersza. Zapis złożony działa przy malejących jednostkach, np. `1 m 2 dm 3 cm 4 mm`. Utracony układ tabeli powoduje prośbę o wiersze i kolumny. Obliczenie z niewykonanym rysunkiem ma stan częściowy oraz oddzielne potwierdzenie rachunku.

Dodano osiem testów granic wejścia. Pełna regresja: **948 testów**. W działającym dashboardzie sprawdzono tabelę, wykonanie częściowe, długość złożoną, przełączanie języka, widok mobilny oraz brak błędów JavaScript. Testy negatywne korzystały z osobnego banku danych. Oryginalne modele nie były modyfikowane.

Źródła: [Koła i okręgi](https://zpe.gov.pl/a/kola-i-okregi/DKZd9Hdak), [Obwody](https://zpe.gov.pl/a/obwody-prostokatow-i-kwadratow/DFgR1mpDP), [Trójkąty](https://zpe.gov.pl/a/trojkaty-i-ich-wlasnosci/D18lmDeFH), [Zadania o trójkątach](https://zpe.gov.pl/a/trojkaty-i-ich-wlasnosci---zadania/DDhL0WkSt), [Wielokąty](https://zpe.gov.pl/a/wielokaty-i-ich-wlasnosci/DBREZOCKP).
