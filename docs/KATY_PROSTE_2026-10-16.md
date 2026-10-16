# Etap 2: kąt, równoległość i prostopadłość

Na prośbę użytkownika etapem drugim są kąty i wzajemne położenie prostych. W dziale Podstawy geometrii dodano uczony czytnik nazw relacji oraz ćwiczenia w stopniach, radianach i gradach. Odległość i położenie punktów pozostają osobnym etapem z dokładnym nauczycielem.

## Podział pracy

Narzędzie dokładnie przelicza jednostki i wyznacza ogólne cechy geometryczne: porównania miary kąta z 0°, 90°, 180° i 360° oraz warunki wynikające z wektorów kierunkowych prostych. **Sieć nie oblicza tych cech i nie odkryła samodzielnie definicji.** Osobny mały model uczy się przypisywać nazwę na podstawie cech. Wynik dodatkowo porównujemy z dokładnym nauczycielem; niezgodność lub mała pewność blokują zaliczenie odpowiedzi.

Rozróżniane są: kąt zerowy, ostry, prosty, rozwarty, półpełny, wklęsły i pełny; różne proste równoległe, proste pokrywające się, prostopadłe i pozostałe przecinające się; nieprawidłowe dane. Proste są rozpatrywane na jednej płaszczyźnie. Proste pokrywające się mają osobną kategorię, zamiast zaliczenia jako dwie różne proste równoległe.

Nie jest to nowy czytnik języka naturalnego ani dowód samodzielnego rozumowania geometrycznego. Opisy słów i definicji są oddzielnym słownikiem. Dalsze uczenie powinno połączyć odczyt opisu z relacjami i sprawdzić nowe parafrazy oraz błędne przesłanki.

## Uczenie i sprawdzian

- 480 przykładów treningowych (278 różnych zestawów danych), 144 DEV (96 różnych), 240 prób odłożonych (153 różne).
- Przed uczeniem: 6/144 DEV. Po uczeniu: 144/144 DEV i 240/240 prób odłożonych; po usunięciu powtórzeń **96/96 DEV i 153/153 odłożonych danych**.
- Powtórzenia występują m.in. przy dokładnych kątach granicznych. Nie traktujemy ich jako różnych zadań ani dodatkowego dowodu uogólniania.
- Zestawy nie współdzielą identycznych żądań wejściowych. Uczenie używa stopni, DEV gradów, a zbiór odłożony radianów; przeliczenie wykonuje narzędzie. Przykłady prostych mają inne współrzędne. **Wzorce cech geometrycznych powtarzają się między zbiorami**, dlatego wynik nie jest sprawdzianem odkrywania nowych praw geometrii.
- Model: 11 cech, warstwa 48 neuronów, 12 klas; ziarno 17102026, 800 kroków. Wagi wybierane wyłącznie przez DEV, zbiór odłożony oceniony po wyborze. Nie zmieniano wag po audycie powtórzeń.
- Osobny checkpoint i manifest. Dotychczasowe modele TSI i pierwszy czytnik pojęć pozostają bez zmian.

## Przykłady i granice

| Dane | Wynik |
|---|---|
| 89,999999° | kąt ostry |
| 90° = π/2 rad = 100 gon | kąt prosty |
| 90,000001° | kąt rozwarty |
| 180° = π rad = 200 gon | kąt półpełny |
| 360° = 2π rad = 400 gon | kąt pełny |
| Wspólne wszystkie punkty dwóch prostych | ta sama prosta |
| Różne proste na płaszczyźnie bez punktów wspólnych | równoległe |
| Przecięcie pod kątem 90° | prostopadłe |

Radiany można podać jako liczbę dziesiętną lub ograniczony zapis z `pi`/`π`, np. `pi/2`, `3*pi/4`. Zapis dziesiętny przybliżający π/2 nie jest automatycznie uznawany za dokładnie 90°. Nie używa się tolerancji zamieniającej prawie równoległe proste w równoległe. Zerowy wektor kierunkowy nie określa prostej. Zakres ćwiczenia kątów: 0–360°, poza zakresem dane są odrzucane.

## Testy i dashboard

27 testów jednostek, parsera ograniczonego zapisu radianów, wartości granicznych, relacji prostych i prawdziwego odczytu nowych wag. Łącznie z podstawami, słownikiem i parserem pudełka: **118 testów**. W przeglądarce potwierdzono granice kąta prostego, radiany, grady, cztery relacje prostych, brak zaliczenia zdegenerowanej prostej, wskazanie nieznanych słów i układ telefonu.

![Etap 2: uczony czytnik i sprawdzenie prostopadłości](katy-proste.png)
