# Matryca wielkości, jednostki i chemia — 16.10.2026

Nowy wybór w menu: **Matryca wielkości i jednostek** (`/akademickie#task=relations`). Użytkownik wskazuje zależność, szukaną wielkość i znane dane. Puste pola są niewiadomymi. Nazwy przedmiotów nie decydują o rachunku: wspólne są struktury zależności i wymiary wielkości.

## Co działa

- 20 modeli: zakup z opłatą, pojemniki, płytki, prostokąt (pole/obwód oraz różnica boków), trójkąt, koło, prostopadłościan, sześcian, walec, ruch jednostajny, gęstość, przepływ, suma, proporcja, rabat; chemia: masa molowa, stężenie molowe, rozcieńczanie i molalność.
- Wybór dowolnego pola modelu jako szukanego. Dane mogą mieć różne zgodne jednostki. Zmiana rodzaju wielkości w sumie/proporcji czyści wartości, aby nie reinterpretować ich po cichu.
- Jednostki wpisywane po nazwie lub skrócie, z podpowiedziami: `centymetr`, `cm`, `km/h`, `kg/m³`, `N·m`, `kWh`, `MPa`, `µA`, `mol/l`, `g/mol`. Nazwy polskie i wybrane angielskie; nie wszystkie odmiany językowe.
- Siedem podstawowych wymiarów SI, jednostki pochodne o nazwach specjalnych, przedrostki od quecto do quetta, złożenia z mnożeniem, dzieleniem, nawiasami i całkowitymi potęgami od −12 do 12. Wielkość liter symboli jest istotna: `mW` i `MW` mają różne skale.
- Przelicznik działa także dla jednostek wielkości, dla których nie ma osobnego modelu zadania, np. napięcia czy ciśnienia. Zgodność wymiarowa nie dowodzi tożsamości znaczenia fizycznego procesów.
- Temperatura: K, °C, °F jako wartości bezwzględne, kontrola zera bezwzględnego. Nie jest to przelicznik różnic temperatur; w złożeniach należy używać K.
- Nieznany wpis pozostaje widoczny. Komunikat wskazuje pole, wpisaną jednostkę lub wartość, przyczynę i dostępne sugestie. Brak danych wskazuje szukaną wielkość i pozostałe niewiadome; system nie zgaduje brakujących danych.

## Wspólne macierze i gałęzie

Równania mają wspólny wektor niewiadomych. Widok pokazuje macierz obecności wielkości w równaniach (0/1) i symboliczną macierz Jacobiego ∂F/∂x. Dla liniowych modeli pokazuje także macierz współczynników A oraz b w A·x=b. Macierz 0/1 nie zastępuje współczynników ani równań.

Dla nieliniowych modeli stosowany jest dokładny solver symboliczny SymPy. Obliczony Jacobian jest pokazywany, ale nie służy obecnie do iteracji Newtona. **Macierz rozwiązań** zawiera osobny wiersz dla każdego kompletnego, dopuszczalnego zestawu wartości, w jednostkach podstawowych wymienionych w nagłówkach. Każdy wiersz przechodzi podstawienie do wszystkich równań, kontrolę rzeczywistości, znaków i całkowitości liczby sztuk. Niekompletnych gałęzi nie oznaczamy jako zweryfikowane rozwiązania. Wynik może być pojedynczy, wieloznaczny, sprzeczny lub wymagać danych.

## Przykłady

| Model / przeliczenie | Dane | Wynik |
|---|---|---|
| Ruch | 120 km, 2 h | 60 km/h |
| Pojemniki | 6 pojemników, łącznie 15 l | 2,5 l na pojemnik |
| Prostokąt | pole 48 m², obwód 28 m | gałęzie boków (6,8) i (8,6) m |
| Gęstość | 1 g/cm³, 2 l | 2 kg |
| Stężenie molowe | 100 mmol, 500 ml roztworu | 0,2 mol/l |
| Masa molowa | 18 g, podana masa molowa 18 g/mol | 1 mol |
| Rozcieńczanie | 2 mol/l, 100 ml → końcowe 500 ml | 0,4 mol/l |
| Molalność | 100 mmol substancji, 500 g rozpuszczalnika | 0,2 mol/kg |
| Energia | 1 kWh | 3 600 000 J |
| Temperatura | 32 °F | 0 °C |

## Granice i znaczenie jednostek chemicznych

`M` oznacza tu mol/l. Molalność dotyczy masy **rozpuszczalnika**, stężenie molowe — objętości **roztworu**. W modelu rozcieńczania zakładamy zachowanie ilości substancji, brak reakcji i końcową objętość nie mniejszą od początkowej.

`ppm` = 10⁻⁶ i `ppb` = 10⁻⁹ udziału bezwymiarowego według jawnej konwencji aplikacji. Trzeba wiedzieć, czy chodzi o udział masowy, objętościowy czy molowy. Nie przeliczamy automatycznie ppm na mg/l. `mol/l` nie jest zgodne wymiarowo z `g/l`: potrzebna jest masa molowa. Aplikacja nie identyfikuje substancji, nie pobiera mas molowych i nie bilansuje reakcji. Ceny różnych walut nie są wymieniane bez kursu.

Nie deklarujemy obsługi każdej historycznej, branżowej lub niejednoznacznej jednostki. Nieznana jednostka wymaga doprecyzowania. Sam solver jest narzędziowym modelem relacji. Osobno wytrenowano dodatkowy czytnik tabel; nie jest parserem dowolnych opisów. [Opis treningu](UCZENIE_TABEL_TSI_2026-10-16.md).

## Weryfikacja

54 testy nowego modułu: wszystkie 20 przykładów modeli, jednostki, prefiksy, temperatura, chemia, błędne dane, brak danych, gałęzie rozwiązań, Jacobian i macierz liniowa. Dotychczasowe 326 testów regresji przeszło po ustawieniu właściwej ścieżki adaptera (pierwsze uruchomienie miało 12 błędów ścieżki środowiska). Test przeglądarkowy obejmuje przelicznik, nieznaną jednostkę, ruch, brak danych, prostokąt, chemię, przełączanie menu i układ mobilny. Nowe funkcje nie zmieniają wag ani chronionych źródeł rdzenia.

Źródła definicji: [BIPM — SI i przedrostki](https://www.bipm.org/en/publications/si-brochure), [IUPAC — stężenie ilościowe](https://goldbook.iupac.org/terms/view/A00295), [IUPAC — molalność](https://goldbook.iupac.org/terms/view/M03970).

Dla ppm/% → ilorazów wybierz rodzaj udziału (masowy, objętościowy lub molowy). Ilorazy masowe i objętościowe nie są utożsamiane. Obsługiwane są też mM, µM i zapis chemiczny np. `mol dm−3`.
