# Zadania tekstowe prowadzące do równań kwadratowych

Stan: 16.10.2026. Rozszerzenie lokalnego trybu „Od opisu do wzoru”.

## Zakres

Dodano trzy rodziny, obok czterech wcześniejszych typów liniowych:

| Rodzina | Zależności | Równanie po podstawieniu |
|---|---|---|
| Pole i różnica boków prostokąta | xy=A, x−y=D, x>0, y>0 | y²+Dy−A=0 |
| Suma i iloczyn dwóch liczb rzeczywistych | x+y=S, xy=P | y²−Sy+P=0 |
| Iloczyn kolejnych liczb całkowitych | xy=P, y=x+1, x,y całkowite | x²+x−P=0 |

Dla liczb kolejnych dodatkowe słowo „dodatnie” zmienia dziedzinę i wynik. Dla sumy i iloczynu system zachowuje obie uporządkowane pary, jeśli treść nie określa kolejności. Jednostki pola: mm², cm² lub m²; różnica boków musi mieć zgodną jednostkę liniową. Nie wykonuje się domyślnego przeliczania jednostek.

Wynik pokazuje współczynniki a, b, c, deltę, pierwiastki algebraiczne, rozwiązania zgodne z treścią i uzasadnienia odrzucenia. Ujemna długość nie jest odpowiedzią. Ujemne liczby całkowite nie są usuwane, jeśli treść ich nie wyklucza. Pierwiastki niecałkowite nie rozwiązują zadania o liczbach całkowitych.

## Przykład

„Pole prostokąta wynosi 48 cm². Jeden bok jest o 2 cm dłuższy od drugiego.”

Model: xy=48, x−y=2. Równanie: y²+2y−48=0. Delta: 196. Pierwiastki: −8 i 6. Para x=−6, y=−8 odpada przez warunek dodatnich długości. Odpowiedź: 8 cm i 6 cm.

## Walidacja

Zaliczone **169 testów**: wszystkie 81 wcześniejszych oraz 88 nowych. Nowe testy obejmują 10 przykładów, 10 przypadków niejasnych lub niemożliwych, 60 wariantów liczb, 7 pełnych wykonań istniejącego walidatora oraz kontrolę uzasadnienia odrzucenia ujemnych długości. Uwzględniono wyniki niewymierne, deltę ujemną, pierwiastek podwójny, zero, mieszane jednostki i dodatkowe warunki.

Walidator porównuje wszystkie pierwiastki równania przed filtrowaniem dziedziny. Warunki wynikające z treści są sprawdzane osobno. Dzięki temu poprawnie odrzucony pierwiastek nie jest traktowany jako awaria narzędzia.

## Dodatkowy test językowy

Zestaw 12 opisów utrwalono przed rozszerzeniem wzorców i nie dopisywano wzorców po obejrzeniu wyników. Odcisk SHA-256: b6cded788dce6a69b15cee4a00f655f0b6cbb9241322a7e47734f38f975b970d.

Spośród 10 jednoznacznych opisów system zbudował 6 poprawnych modeli, a w 4 przypadkach poprosił o doprecyzowanie. Dwa przypadki kontrolne z dodatkowym warunkiem lub niespójnymi jednostkami zatrzymano prawidłowo. Nie wygenerowano błędnego modelu. To mały zestaw przygotowany przez autora implementacji, nie niezależne badanie reprezentatywnej populacji zadań ani dowód ogólnego rozumienia.

Pełne wyniki: `KWADRATOWE_LANGUAGE_RESULT.json`. Ten wynik pokazuje przede wszystkim brak obsługi części poprawnych sformułowań.

## Ograniczenia

Nadal działa kontrolowana gramatyka, nie nowo wytrenowany model językowy TSI. Nie zmieniono wag menedżera ani rdzenia. Parametry symboliczne, nierówności, trygonometria, ciągi i ogólne zadania o funkcjach nie zostały wdrożone w tym etapie. Jest to wprowadzenie do zadań licealnych z równaniami kwadratowymi, nie pokrycie całego programu liceum.


## Wdrożenie lokalne

Powtórzono wszystkie 169 testów w docelowym repozytorium: bez błędów i pominięć. Przeglądarka potwierdziła 5 nowych przykładów, deltę, filtrowanie dziedziny, odmowę nieobsługiwanej parafrazy oraz układ 1366 i 390 pikseli bez błędów JavaScript. Sprawdzono zgodność SHA-256 11 chronionych plików i aktywnego checkpointu. Nie wykonywano nowego treningu ani ponownej oceny wcześniejszych zestawów 80/240 poleceń menedżera. Raport: KWADRATOWE_VERIFICATION.json.
