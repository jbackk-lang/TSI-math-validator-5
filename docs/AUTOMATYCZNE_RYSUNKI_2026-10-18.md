# Automatyczne rysunki do zadań — 2026-10-18

Panel dobiera grafikę z wyniku odczytu i solvera, bez osobnego polecenia rysowania.

- Dwie liczby: oś liczbowa dla par rozwiązań wymiernych.
- Geometria ilościowa: schematy siedmiu figur, dane i wyznaczone wymiary.
- Pudełka: schemat prostopadłościanu z oznaczeniem uwzględnionego, pominiętego lub nieustalonego dna i pokrywki.
- Optymalizacja: przybliżony wykres funkcji celu, punkty stacjonarne i otwarte/zamknięte końce przedziału. Przy nieograniczonej dziedzinie oznaczony wycinek.
- Matryca działań: kolejne wiersze i odwołania do argumentów.
- Pytania geometryczne: rysunek dostępnego przykładu lub kontrprzykładu z jego współrzędnych albo trzech kątów trójkąta.
- Inne rozpoznane modele: schemat wielkości, zależności i wyników, gdy wynik udostępnia wystarczające dane.

Grafika pojawia się u góry wyniku. Edycja treści usuwa poprzedni rysunek. Podpisy wspierają PL/EN.

To automatyczna warstwa wizualizacji rozpoznanego modelu, a nie nowa umiejętność generowania dowolnego rysunku przez sieć neuronową. Nie rozszerza rozumienia nieobsługiwanych opisów. Nie zgaduje brakujących warunków. Schematy figur i bryły nie są w skali; wykres jest numerycznym podglądem dokładnego rozwiązania. Obsługiwany zapis wykresu jest ograniczony do arytmetyki, potęg, pi i pierwiastka. Nie jest wykonywany kod z treści zadania.

Weryfikacja: siedem rzeczywistych wyników parserów/solverów (liczby, prostokąt optymalizacyjny, suma kwadratów, pudełko, zakupy, trójkąt, koło), siedem schematów figur oraz kontrole ujemnych/ułamkowych liczb, otwartych dziedzin, nieobsługiwanych wyrażeń i sprzecznych danych. Testy te dotyczą warstwy rysowania, nie dowodzą rozumienia dowolnej treści.
