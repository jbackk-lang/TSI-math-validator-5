# Uczenie czytnika tabel TSI — 16.10.2026

Wytrenowano nowy, dodatkowy moduł menedżera TSI: sieć czytającą tabelę wielkości. Rozpoznaje jedną z 20 rodzin relacji albo brak obsługi i przypisuje wiersze do niewiadomych. Nie zastępuje dotychczasowego menedżera równań ani jego wag. Nie jest treningiem całego starego rdzenia.

W dashboardzie: **Matryca wielkości i jednostek → TSI uczony — rozpoznaj tabelę**. Wpisz nazwę, wartość i jednostkę w każdym wierszu. Dokładnie jedna wartość pozostaje pusta. TSI pokazuje dopasowany model, przypisanie oryginalnych nazw do ról oraz wynik sprawdzony przez solver. Przy powtarzającym się „ilość” komunikat wymienia oddzielnie np. **2 kg, 5 kg i (szukana wartość) kg** oraz prosi o określenie ich ról.

## Co było uczone

Sieć o architekturze niezależnej od kolejności wierszy otrzymuje cechy nazw (wyrazy i fragmenty znakowe), siedem wymiarów jednostek, oznaczenie waluty/liczby sztuk oraz informację o pustej wartości. Uczy się rodziny relacji i wiązań zmiennych. **Nie otrzymuje etykiety rodziny, identyfikatorów ról ani odpowiedzi jako cech wejściowych. Nie przewiduje wyniku liczbowego**: liczby liczy dokładny nauczyciel/solver. Przeliczenie skali jednostek także jest formalne, a nie wyuczone.

Przygotowano 1188 przykładów treningowych, 396 kontrolnych DEV i 396 końcowych. To dane syntetyczne: znane słownictwo nazw w nowych kombinacjach. Podział usuwa wspólne reprezentacje tabel, ignorując samą zmianę liczb, skali zgodnych jednostek i kolejności wierszy. Zbiór końcowy zapisano przed treningiem; nie służył do wyboru kroku, ziarna ani progu. Nie jest to test dowolnego języka naturalnego ani zadań napisanych przez niezależnych użytkowników.

Trzy treningi, po 800 aktualizacji, AdamW 0,002, batch 64. Monitorowanie DEV co 50 kroków, zatrzymanie przy spadku o 10 punktów procentowych od maksimum po kroku 200. Nie wystąpił taki spadek. Wybór: najlepszy DEV, następnie jego strata; zachowano wybrane checkpointy.

| Ziarno | Wybrany krok | DEV: rodzina i wszystkie role | Test końcowy: rodzina i wszystkie role |
|---|---:|---:|---:|
| 1610 | 700 | 396/396 | 396/396 |
| 1611 | 750 | 396/396 | 396/396 |
| 1612 | 800 | 396/396 | 396/396 |

Przed uczeniem pełne przypisanie DEV wynosiło 0/396 dla każdej inicjalizacji. Wybrano ziarno 1612 według DEV; jego odłożony test to 396/396. Jest to wynik samego uczonego czytnika na opisanym zbiorze.

## Sieć i formalny nauczyciel

Sam dobry wynik klasyfikacji nie wystarcza do wdrożenia. Kontrola wykonania ujawniła brak jednostki `1` dla rabatu zapisanego ułamkiem oraz słabsze rozpoznanie niepełnych tabel prostokąta i nowego określenia drogi. Poprawiono błąd jednostki. Nie zmieniano wag na podstawie tych prób.

Do odczytu dodano jawną kontrolę formalną: zgodność wymiarów, jednoznaczne wiązanie wierszy, respektowanie dokładnych nazw pól danego modelu i obecność wielkości wyróżniającej model szczególny (np. różnicy boków lub mnożnika proporcji). Sieć szereguje dopuszczalne przypisania; zbyt mała przewaga propozycji oznacza doprecyzowanie. Wyświetlana ocena po tej kontroli nie jest skalibrowanym prawdopodobieństwem prawdy. Kontrola nie dowodzi zgodności modelu z intencją dowolnego użytkownika.

Po kontroli formalnej: **360/360 przyjętych zadań obsługiwanych rodzin** przeszło porównanie z nauczycielem i dokładne podstawienie. Pozostałe 36 przypadków końcowych dotyczyło braku obsługi. Dodatkowa próba **60/60** z nowymi liczbami i skalami jednostek przeszła dla całego połączenia sieci i nauczyciela. Ta próba używa znanych nazw pól i nie jest dowodem nowej zdolności językowej samej sieci.

Siedem eksploracyjnych scenariuszy (nowe nazwy jabłek, trasy, substancji i działki, powtórzone „ilość”, nieznane `msz`, nieobsługiwane prawo Ohma) dało 7/7 poprawnych rozwiązań albo właściwych doprecyzowań. Scenariusze zapisano przed oceną końcową, ale po rozpoczęciu treningów; nie były używane do uczenia ani wyboru checkpointu. Ten mały test nie potwierdza uniwersalności. Pierwotny odczyt bez nowych kontroli miał 6/7 w tej próbie i 54/60 w próbie liczb/jednostek; nie należy tych wyników utożsamiać z wynikiem końcowego połączenia.

## Bezpieczeństwo pomiaru i zakres

65 testów nowych modułów obejmuje 20 modeli, jednostki, temperaturę i chemię, macierze gałęzi/Jacobiego, niezależność od kolejności i wartości liczbowych w czytniku, kontrolę wymiarów i doprecyzowania konkretnych wartości. Dotychczasowe 326 testów regresji przeszło. Przeglądarka sprawdziła rozpoznanie chemii, nowych nazw ruchu, komunikaty „ilość”, menu i telefon. Stare wagi, aktywny menedżer oraz chronione źródła są identyczne bajtowo.

Dane, kod treningu, protokół, trzy checkpointy, wybrany model i raporty pozostają lokalnie oraz w portable. Publiczne repo zawiera opis i obrazy. Aktualizacja nie oznacza samodzielnego uczenia w tle, rozumienia dowolnego opisu ani samodzielnej neuronowej arytmetyki.

SHA-256 wybranego modelu: `6e79004730897d7e6b05bafcbdc28fe98fac0b8425ae6b08ef6767c56fd28d69`.

W końcowym sprawdzeniu uruchamiania wykryto dwie kopie serwera na porcie 8795. Pozostawiono jedną i dodano wyłączność portu. Pięć dodatkowych testów potwierdziło blokadę duplikatu i limity czasu: uczony czytnik ma co najmniej 60 s na zimny start, pozostałe narzędzia zachowują dotychczasowe limity. MUZ na 8796 pozostał dostępny.
