# TSI-math-validator-5

Stan: **16 października 2026**. Lokalny warsztat matematyczny z uczonym menedżerem TSI oraz jawnymi narzędziami obliczeniowymi SymPy.

To repozytorium GitHub zawiera **dokumentację i zrzuty ekranu**. Kod, wagi i dane treningowe pozostają w oddzielnym repozytorium lokalnym.

## PL / EN i portable

Przełącznik **PL / EN** zmienia interfejs, komunikaty i opisy wyników oraz zapamiętuje wybór w przeglądarce. Wpisane dane pozostają bez zmian. Polecenia i opisy zadań tekstowych nadal muszą być po polsku; wzory i audyt nie wymagają polskiej treści.

Przygotowano lokalną wersję **portable Windows x64 z pełnym kodem, modelami, Pythonem i bibliotekami**. Po rozpakowaniu całości: `START.bat`; zatrzymanie: `ZATRZYMAJ.bat`. Nie wymaga instalowania Pythona ani pobierania modeli. Pakiet z kodem pozostaje lokalnie; nie jest plikiem do pobrania z tego repozytorium dokumentacyjnego. [Zakres i testy portable](docs/PL_EN_PORTABLE_2026-10-16.md).

![English interface: solution audit](docs/audit-en.png)

## Matryca wielkości, jednostki i uczony TSI

Nowy wybór **Matryca wielkości i jednostek** obejmuje 20 modeli, dowolne pole jako niewiadomą i różne zgodne jednostki. Nazwę lub skrót jednostki można wpisać z podpowiedziami, np. `centymetr`, `km/h`, `kg/m³`, `mol/l`, `g/mol`. Dostępne są jednostki SI z przedrostkami, jednostki złożone, temperatury bezwzględne i chemia: masa molowa, stężenie, rozcieńczanie, molalność. Wynik pokazuje równania, wspólne niewiadome, macierz zależności, Jacobian i macierz sprawdzonych rozwiązań.

**Wytrenowano dodatkowy czytnik tabel menedżera TSI.** W trybie „TSI uczony — rozpoznaj tabelę” rozpoznaje rodzinę i przypisuje wiersze. W trzech treningach: 396/396 odłożonych tabel dla samego czytnika (syntetyczny test nowych kombinacji znanego słownictwa). Sieć wsparta jawną kontrolą nazw i jednostek oraz dokładnym solverem: 360/360 przyjętych zadań końcowych i 60/60 dodatkowych prób nowych liczb/jednostek. Liczb nie liczy sieć; nie jest to uniwersalne rozumienie opisów. Niejasności wskazują konkretne nazwy, wartości i jednostki.

[Modele i jednostki](docs/RELACJE_JEDNOSTKI_2026-10-16.md) · [Trening, wyniki i ograniczenia](docs/UCZENIE_TABEL_TSI_2026-10-16.md).

![Uczony TSI: tabela i macierz rozwiązań](docs/tsi-uczony-tabela.png)

## Słowa i ich znaczenia

Lekcja koła i okręgu: dziewięć nowych pojęć oraz przycisk **Wyjaśnij słowa z treści**. [Zakres lekcji i ograniczenia](docs/KOLO_OKRAG_SLOWNICTWO_2026-10-16.md).

Dodano rozszerzalny słownik pojęć pudełka: **23 pojęcia i 139 zapisanych form wyrazów**. W zadaniach tekstowych można jawnie nauczyć nowej nazwy dna lub pokrywki. Wynik pokazuje odczytane znaczenia, negacje, poprawki i konkretne braki. „Bez przykrywki” i „nie pomijaj przykrywki” prowadzą do przeciwnych warunków. Jest to symboliczna warstwa z nadzorowanym słownikiem, bez nowego treningu wag ani uniwersalnego rozumienia języka. [Zakres, przykłady i sprawdziany](docs/SLOWA_ZNACZENIA_2026-10-16.md).

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
| Audyt rozwiązania | Równoważność kolejnych równań, utracone/dodane rozwiązania, pierwszy błędny krok; tożsamości i kontrprzykłady; trzy oceny i raport JSON |
| Diagnostyka zapisu | Pole i pozycja błędu, wyjaśnienie, podpowiedź i zaznaczenie w tekście; błędny wpis pozostaje do poprawy |

Parser opisów i narzędzia obliczeniowe są regułowe. Uczony czytnik tabel jest osobnym modułem menedżera; nie zmienia wag pierwotnego rdzenia TSI. Kalkulator logiki odtwarza etykiety użyte w treningu; nie wywołuje sieci logicznej.

![Główny dashboard z rozwijanym menu](docs/dashboard-menu.png)

## Audyt własnego rozwiązania

Wybierz **Audyt rozwiązania i kontrprzykłady** i wpisz każde równanie w osobnym wierszu. Przejście `x*(x-1)=0` → `x-1=0` zostanie obalone ze wskazaniem utraconego x=0. Dla `sqrt(x^2)=x` w liczbach rzeczywistych dostaniesz kontrprzykład; przy x≥0 tożsamość zostanie potwierdzona. Można wybrać założenia i pobrać raport z wersją silnika oraz sumą źródła. Wyniki mają oceny: potwierdzone, obalone, nierozstrzygnięte.

Zakres: jedna zmienna, równania wymierne stopnia do 6 po uproszczeniu; wybrane tożsamości i próbkowane kontrprzykłady. To nie jest ogólny asystent dowodów. Brak kontrprzykładu nie dowodzi poprawności. [Zakres i przykłady audytora](docs/AUDYT_ROZUMOWANIA_2026-10-16.md).

![Audyt: rozwiązanie utracone przy dzieleniu](docs/audyt-utraty.png)

Wyniki obliczeń wyświetlane są równolegle w zapisie matematycznym i technicznym do skopiowania, np. **x³/3 + C** i `x**3/3 + C`.

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
| Poprzedni zestaw regresji diagnostyki i wykresów | 62/62 |
| Obecny pełny zestaw: zadania, optymalizacja, narzędzia, diagnostyka i audyt | **326/326** |
| Testy audytora, zawarte w pełnym zestawie | 37/37 |
| Logika kalkulatora względem oryginalnych etykiet treningowych | 54/54 kombinacje |

Zestawy 261, 62 i 326 obejmują częściowo te same sprawdzenia; nie należy ich sumować. Historycznych 72/80 i 240/240 nie zmierzono ponownie w tym etapie. Sprawdzono również rzeczywiste formularze, wskazanie błędu i poprawę wpisu, wykresy, nawigację oraz widok mobilny. Kontrola SHA-256 potwierdza zachowanie 11 chronionych plików i aktywnego checkpointu.

90% dotyczy syntetycznego zestawu wyboru celów, nie dowolnych poleceń użytkowników ani całej matematyki. Parser treści ma kontrolowane wzorce; poprawny rachunek nie dowodzi poprawnej interpretacji dowolnego opisu. Sprawdzenie przez tę samą bibliotekę nie jest niezależnym dowodem kompletności rozwiązania. Ogólny czat, autonomiczny planista i pełny zakres matematyki akademickiej pozostają poza potwierdzonym zakresem.

## Uruchomienie lokalne i szczegóły

W działającej instalacji panel jest pod `http://127.0.0.1:8795/`. Ten adres działa wyłącznie na komputerze z uruchomionym serwerem; GitHub przechowuje dokumentację, nie aplikację. W modelach językowych wykorzystywany jest również wcześniej uczony HerBERT.

[Historia pracy](HISTORIA_SI_2026-10-11.md) · [Etap akademicki](docs/ETAP_AKADEMICKI_2026-10-16.md) · [Etap kwadratowy](docs/ETAP_KWADRATOWY_2026-10-16.md) · [Diagnostyka i wykresy](docs/DIAGNOSTYKA_2026-10-16.md) · [Pomiary menedżera](docs/WYNIKI_2026-10-15.md) · [Pochodzenie komponentów](docs/POCHODZENIE.md).
