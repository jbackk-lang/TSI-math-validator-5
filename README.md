# TSI-math-validator-5

**Stan: 23 października 2026.** Lokalny warsztat do obliczeń, sprawdzania rozwiązań i nauki matematyki.

## Co działa

- Równania i funkcje: rozwiązania, dziedzina, pochodne, zera, ekstrema, asymptoty i wykresy w obsługiwanym zakresie.
- Całki oznaczone i nieoznaczone: wykresy funkcji i pierwotnej, kontrola pochodną, dziedzina, osobliwości, pole ze znakiem i geometryczne; stałe π i e, zapisy `^` oraz `**`.
- Zadania tekstowe: dane, niewiadome, model zależności, rozwiązanie i rysunek dla rozpoznanych konstrukcji. Dowolna podmiana treści nadal może wymagać doprecyzowania.
- Geometria: 19 modeli, figury i bryły, wyznaczanie niewiadomej, jednostki, siatki i rysunki; tryby obliczeń, wiadomości i nauki. Fizyka: cztery modele mechaniki pojedynczego pręta.
- Macierze, logika dwustanowa i trójstanowa oraz audyt kroków ucznia.
- Import PDF, zdjęć, TXT/MD i DOCX do korekty wzoru; mini klawiatura matematyczna. Wynik OCR wymaga sprawdzenia.
- Edytowalne przykłady, lokalna historia, powtórki po błędach, panel poprawek z hasłem i wycofywaniem zmian.
- Słownik: 3242 hasła, wyszukiwanie i alfabet; 2932 rozwinięcia oraz 129 odnośników MathWorld.

## Uruchomienie i przykłady

W wersji portable użyj `START.bat`. W instalacji roboczej uruchom dotychczasowy plik startowy; standardowy panel jest pod `http://127.0.0.1:8795/`. Portable wybiera osobny wolny port od 8797.

| Temat | Dane do wpisania |
|---|---|
| Równanie | `x^2 - 64 = 0` |
| Całka oznaczona | `x^2`, granice `0` i `3` — wynik `9` |
| Zadanie tekstowe | `Dwie liczby mają sumę 13 i iloczyn 40.` — liczby `5` i `8` |
| Geometria | Prostokąt, boki `4 cm` i `3 cm`, pole — `12 cm²` |

## Ostatnie sprawdzenia

**7/7 kontroli matematycznych** po konsolidacji: powtarzane zadanie tekstowe, zmienione liczby, równanie, geometria i całka. Kontrola HTTP potwierdziła wyniki oraz odrzucenie błędnego zapisu. To test tych przypadków, nie całego zakresu aplikacji.

Pomiar lokalny: pierwsze zadanie tekstowe **48,891 s**, kolejne **0,266–0,469 s**; równanie **0,031 s**, geometria **0,360 s**, całka **1,250 s**. Pierwsze uruchomienie nadal ładuje biblioteki i modele; czasy zależą od sprzętu i zadania.

## Podgląd

![Warsztat matematyczny](docs/dashboard-menu.png)

![Edytowalne przykłady całek](docs/edytowalne-przyklady.png)

## TSI — stan na 23 października 2026

Obliczenia i odczyt obsługiwanych poleceń korzystają ze wspólnego modułu TSI. Czytnik i narzędzia pozostają w uruchomionym procesie, co usuwa ich wielokrotne ładowanie przy kolejnych zadaniach. Moduł matematyczny znajduje się wewnątrz TSI; aplikacje korzystają z jego interfejsu.

Aktywny moduł dowodowy: **TSI-DUAL-TASK-V3-5f8069b8**, **10 227 859 parametrów**, plik wag **41 276 171 bajtów (39,36 MiB)**. To rozmiar tego checkpointu, a nie wszystkich czytników, bibliotek i aplikacji. Dodatkowe czytniki, modele dziedzinowe oraz solvery są dołączane osobno.

Nowe wagi swobodnej rozmowy pozostają w treningu i **nie są wdrożone**. Wynik 24/24 na wybranym zestawie kolorów i godzin nie potwierdził ogólnej poprawy: szerszy sprawdzian dał 9/12 przed i po korekcie. Nadal rozwijane są wiązanie cech z osobami, aktualizacja faktów i pełny zapis wartości.

## Portable — Windows x64

Paczka zawiera kod źródłowy, aktywne modele, lokalny Python i biblioteki. Rozpakuj cały ZIP do katalogu z prawem zapisu i uruchom **START.bat**. Zatrzymanie: **ZATRZYMAJ.bat**. Nie potrzeba innych katalogów projektów ani instalowania Pythona. Zachowaj całą strukturę folderów.

Portable przechowuje własne dane wykonania w `app/runtime`. Archiwum startowe nie zawiera prywatnych dokumentów bankowych, danych użytkownika, haseł panelu, tokenów, historii Git i katalogów treningu. Baza użytkownika istniejącej lokalnej wersji portable jest zachowywana podczas aktualizacji folderu; ZIP przeznaczony do przenoszenia pozostaje czysty.

Rozmiary składników znajdują się w `PACKAGE_INFO.json` wewnątrz paczki. Rozmiar ZIP i jego SHA-256 zapisuje raport `PORTABLE_PACKAGES_2026-10-23.json` obok archiwów. Zewnętrzne odnośniki słownika wymagają internetu. Import obrazów wymaga dostępnego lokalnego OCR; obecność i działanie OCR są wykazywane w raporcie kontroli paczki.

## Historia

Poprzedni README i opis wcześniejszych etapów: [archiwum dokumentacji](docs/archiwum/README_przed_2026-10-23.md). [Aktualna integracja i sprawdzenia](docs/INTEGRACJA_TSI_2026-10-23.md).
