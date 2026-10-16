# Matryca ról i zależności

Stan: 16 października 2026. Lokalna strona: **http://127.0.0.1:8795/matryca**, dostępna także z nagłówka strony Geometria. Nowy widok jest po polsku.

## Co robi

Buduje strukturę działań z wejścia, zamiast wybierać gotowe pełne zadanie. Każda liczba, niewiadoma i działanie otrzymuje osobny wiersz. Argumenty odwołują się do wyników innych wierszy. Dzięki temu `2 × (3 + 4)` i `2 × 3 + 4` mają inne zależności i wyniki. Dzielenie ma jawne role licznika i mianownika, potęgowanie — podstawy i wykładnika.

Widok pokazuje macierz, kolejność obliczeń, zapis z nawiasami, wyniki pośrednie oraz niewiadome do uzupełnienia. Ułamki i dziesiętne wartości są liczone dokładnie. Dopuszczono +, −, ×, ÷, potęgi całkowite od −12 do 12 i zmienne. Dostępne są oba zapisy potęg: `^` i `**`.

## Automatyczna pętla

Tryb automatyczny ma najwyżej trzy próby:

1. Odczyt jawnego wzoru z regułami kolejności działań.
2. Odczyt kontrolowanego opisu nazw działań, również zagnieżdżonego.
3. Eksperymentalny uczony czytnik ról licznika i mianownika, jeśli tekst zawiera takie wskazówki.

Każda metoda samodzielnie buduje macierz. Pętla nie przepisuje zadania, nie dopowiada danych i nie zmienia wag. Zgodna struktura jest sprawdzana pod kątem zależności, liczby argumentów i dziedziny działań. Różne struktury powodują prośbę o doprecyzowanie. Brak wartości wskazuje nazwę niewiadomej. Dzielenie przez zero, cykle, brakujące odwołania i niepowiązane wiersze są odrzucane.

Wynik eksperymentalnego czytnika ról jest **propozycją wymagającą sprawdzenia i potwierdzenia przez użytkownika** przed udostępnieniem wyniku liczbowego. Nieznane słowa, niepewna odpowiedź i dwukrotne przypisanie tej samej roli zatrzymują próbę. Długości boków należy podawać dodatnie, w jednej jednostce. Ten widok służy do analizy ilorazu; nie jest pełnym sprawdzianem geometrii trójkąta.

## Przykłady

| Wejście | Wynik / zachowanie |
|---|---|
| `2 × (3 + 4)` | 14; suma jest argumentem mnożenia |
| `2 × 3 + 4` | 10; iloczyn jest argumentem dodawania |
| `−3^2` / `(−3)^2` | −9 / 9 |
| `(1/2)/(3/4)` | 2/3 |
| `pomnóż sumę 3 i 4 przez 2` | 14 |
| `podziel różnicę 10 i 2 przez sumę 1 i 3` | 2 |
| `2 × (x + 3)` | wskazuje brak wartości x; po wpisaniu 1/2 wynik 7 |
| `suma 3 i` | wskazuje brak drugiego argumentu |
| `U góry ilorazu jest przyprostokątna naprzeciw kąta. Na dole ilorazu jest przyprostokątna przy kącie.` | propozycja przypisania boków do licznika i mianownika, następnie definicja tangensa i pola wartości |

## Nauka i ograniczenia

Wcześniejsze douczanie klasyfikatora całych opisów nie poprawiło nowych sformułowań: 19/24 przed i po nauce, z większą liczbą pewnych błędów. Wariant odrzucono. Osobny eksperyment uczył **rolę i obiekt pojedynczego zdania**, a nie nazwę funkcji całego opisu: 48 zdań treningowych, 12/12 DEV, 18/18 nowych zdań. Z 27 par nowych zdań w dwóch kolejnościach uzyskano 54/54 poprawne złożenia; przy progu pewności obu części 0,9 zaakceptowano 40, a 14 wymagało doprecyzowania. To współdzielone, syntetyczne przykłady, nie 54 niezależne zadania. W aplikacji obowiązuje dodatkowo kontrola słownictwa, więc nie wszystkie nowe parafrazy z eksperymentu muszą zostać przyjęte.

Obliczenia i budowę zależności wykonuje jawne narzędzie. Nie nauczono sieci ogólnej arytmetyki. Kontrolowany parser opisów jest regułowy; uczony czytnik pracuje tylko w osobnym trybie ról. Dotychczasowy czytnik całych opisów trygonometrycznych z wynikiem 95/96 pozostaje nieaktywny. Matryca nie oznacza rozumienia dowolnych zadań ani samodzielnego wiarygodnego uczenia się na własnych odpowiedziach.

Sprawdziany: **54 testy matrycy i pętli**; dodatkowy audyt istniejącego narzędzia rachunkowego: **24/24 wyników i 4/4 odrzuconych błędnych zapisów**. Osobno sprawdzany jest działający interfejs i eksperymentalny czytnik. Kod, wagi, protokoły z danymi i szczegółowe raporty pozostają lokalnie.

Aktualizacja dotyczy uruchomionej lokalnej aplikacji. Wcześniej przygotowane archiwum portable nie jest potwierdzeniem obecności tej zmiany.
