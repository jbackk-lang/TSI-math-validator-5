# TSI-math-validator-5

Stan: **16 października 2026**. Lokalny warsztat matematyczny z uczonym menedżerem TSI oraz jawnymi narzędziami obliczeniowymi SymPy.

To repozytorium GitHub zawiera **dokumentację i zrzuty ekranu**. Kod, wagi i dane treningowe pozostają w oddzielnym repozytorium lokalnym.

## Co robi

Wspólne rozwijane menu prowadzi do wszystkich rodzajów zadań. Formularz i wynik są obok siebie, a na telefonie jeden pod drugim. Wyniki badań są w zwijanej sekcji.

| Zadanie | Obecny zakres |
|---|---|
| Równania i wykresy | Rozpoznanie celu polskiego polecenia, osobne wyrażenie, pierwiastki i sprawdzenie podstawieniem |
| Zadania tekstowe | Siedem kontrolowanych rodzin liniowych i kwadratowych; niewiadome, równania, delta i sprawdzenie dziedziny |
| Optymalizacja | Cztery wzorce: pole prostokąta, pudełko z arkusza, suma kwadratów, funkcja kwadratowa na przedziale; pochodne, punkty stacjonarne i brzegi |
| Całki | Nieoznaczone z C i sprawdzeniem pochodną; oznaczone na ciągłym, skończonym przedziale |
| Wykresy całek | Funkcja podcałkowa; dla nieoznaczonej także pierwotna przy C=0, gdy potwierdzona; dla oznaczonej przedział i zacieniowany obszar |
| Macierze do 6 × 6 | Suma, iloczyn, transpozycja, wyznacznik, odwrotność, rząd i układy A·x=B; wykrywanie osobliwości i sprzeczności |
| Logika | Klasyczna oraz trójstanowa silna Kleene’a: NOT, AND, OR, XOR, IMPLIES, EQUIV; jawne tabele działań |
| Diagnostyka zapisu | Pole i pozycja błędu, wyjaśnienie, podpowiedź i zaznaczenie w tekście; błędny wpis pozostaje do poprawy |

Nowe narzędzia i parser opisów są regułowe. **Nie oznaczają nowych wyuczonych zdolności rdzenia TSI.** Kalkulator logiki odtwarza etykiety użyte w treningu; nie wywołuje sieci logicznej.

![Główny dashboard z rozwijanym menu](docs/dashboard-menu.png)

## Błąd: gdzie, co i jak poprawić

Przed obliczeniem sprawdzane są nawiasy, składnia i argumenty funkcji. Komunikat podaje wiersz, kolumnę, opis i podpowiedź. Przycisk „Pokaż miejsce błędu” zaznacza wskazany fragment. Zmiana wpisu usuwa nieaktualne wskazanie; system nie poprawia sam treści.

Przykłady: `2*(x+3` → wskazanie niezamkniętego nawiasu; `x + * 2` → błędny operator; `sin()` → brak argumentu. Dla macierzy sprawdzane są również długości wierszy, elementy, mianowniki i zgodność wymiarów. Nie każdemu błędowi matematycznemu odpowiada jeden znak: przy niezgodnych wymiarach zaznaczana jest macierz lub wiersz.

![Diagnostyka brakującego nawiasu](docs/blad-nawiasu.png)

## Przykłady

| Wybór zadania | Dane | Wynik |
|---|---|---|
| Równania i wykresy | Polecenie: „rozwiąż równanie i pokaż wykres”; wyrażenie: `x^2-64` | −8 i 8, sprawdzenie oraz wykres |
| Zadania tekstowe | „Dwie liczby mają sumę 13 i iloczyn 40.” | Równanie kwadratowe, liczby 5 i 8 z zachowaniem możliwych przypisań |
| Optymalizacja | „Prostokąt ma obwód 40 cm. Wyznacz największe pole.” | Boki 10 cm, pole 100 cm² |
| Całka nieoznaczona | `x^2` | `x^3/3 + C`, sprawdzenie pochodną i dwa wykresy |
| Całka oznaczona | `x^2`, od 0 do 3 | 9 i wykres funkcji na przedziale |
| Macierze | `[[1,2],[3,4]]`, wyznacznik | −2 |
| Logika trójstanowa | `F AND U` | F; U oznacza nieznane |

![Całka nieoznaczona z wykresami](docs/calka-z-wykresem.png)

![Całka oznaczona z zaznaczonym obszarem](docs/calka-oznaczona.png)

Całki przyjmują zmienną x, funkcje sin, cos, tan, exp, log, sqrt, Abs i stałe pi, E. Potęgi w tym formularzu są ograniczone do liczbowych wykładników od −12 do 12. Pierwotne sprawdzane są lokalnie na składowych dziedziny. Całki niewłaściwe, nieskończone granice i niepotwierdzona ciągłość są poza tym etapem. Wykres jest przybliżonym podglądem numerycznym; zacieniowany obszar nie zastępuje całki uwzględniającej znak i kierunek granic.

## Potwierdzone wyniki i ich znaczenie

| Sprawdzenie | Wynik |
|---|---:|
| Historyczny test pięciu celów wyuczonego menedżera, 15.10.2026 | 72/80 — 90% |
| Historyczny test zachowania wcześniejszych odpowiedzi | 240/240 |
| Etap akademicki i wcześniejsze zadania, przed diagnostyką | 261/261 |
| Bieżący zestaw regresji narzędzi, transportu, diagnostyki i danych wykresu | 62/62 |
| Logika kalkulatora względem oryginalnych etykiet treningowych | 54/54 kombinacje |

Wyniki 261 i 62 obejmują częściowo te same sprawdzenia; nie należy ich sumować. Historycznych 72/80 i 240/240 nie zmierzono ponownie w tym etapie. Sprawdzono również rzeczywiste formularze, wskazanie błędu i poprawę wpisu, wykresy, nawigację oraz widok mobilny. Kontrola SHA-256 potwierdza zachowanie 11 chronionych plików i aktywnego checkpointu.

90% dotyczy syntetycznego zestawu wyboru celów, nie dowolnych poleceń użytkowników ani całej matematyki. Parser treści ma kontrolowane wzorce; poprawny rachunek nie dowodzi poprawnej interpretacji dowolnego opisu. Sprawdzenie przez tę samą bibliotekę nie jest niezależnym dowodem kompletności rozwiązania. Ogólny czat, autonomiczny planista i pełny zakres matematyki akademickiej pozostają poza potwierdzonym zakresem.

## Uruchomienie lokalne i szczegóły

W działającej instalacji panel jest pod `http://127.0.0.1:8795/`. Ten adres działa wyłącznie na komputerze z uruchomionym serwerem; GitHub przechowuje dokumentację, nie aplikację. W modelach językowych wykorzystywany jest również wcześniej uczony HerBERT.

[Historia pracy](HISTORIA_SI_2026-10-11.md) · [Etap akademicki](docs/ETAP_AKADEMICKI_2026-10-16.md) · [Etap kwadratowy](docs/ETAP_KWADRATOWY_2026-10-16.md) · [Diagnostyka i wykresy](docs/DIAGNOSTYKA_2026-10-16.md) · [Pomiary menedżera](docs/WYNIKI_2026-10-15.md) · [Pochodzenie komponentów](docs/POCHODZENIE.md).
