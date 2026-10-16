# Etap akademicki — 16 października 2026

Dodano lokalną stronę `/akademickie`: całki, macierze i logika klasyczna oraz trójstanowa. To warstwa narzędziowa; nie trening ani dowód nowych umiejętności wyuczonego rdzenia TSI.

## Zakres

- Całki nieoznaczone: jawna funkcja zmiennej x; wynik z C, sprawdzenie różniczkowaniem. Funkcje sin, cos, tan, exp, log, sqrt, Abs; liczby wymierne, potęgi od -12 do 12, pi, E. Pierwotne lokalne na składowych dziedziny rzeczywistej.
- Całki oznaczone: skończone granice liczbowe i potwierdzona ciągłość na całym przedziale. Osobliwości i całki niewłaściwe wymagają kolejnego etapu; brak wyniku zamkniętego jest jawnie nierozstrzygnięty.
- Macierze do 6×6: suma, iloczyn, transpozycja, wyznacznik, odwrotność, rząd i układ A*x=B. Dokładne ułamki; rozróżnienie macierzy osobliwej, układu sprzecznego i nieoznaczonego. Odwrotność i rozwiązanie sprawdzane dokładnymi tożsamościami.
- Logika: NOT, AND, OR, XOR, IMPLIES, EQUIV. T=prawda, F=fałsz, U=nieznane. Logika klasyczna lub silna Kleene’a. Jawna tabela operatora. Reguły porównano ze wszystkimi 54 etykietami funkcji gold w oryginalnym train_logic_foundation.py, bez uruchamiania treningu. Kalkulator nie wywołuje wyuczonej sieci logicznej.
- Optymalizacja: cztery kontrolowane wzorce opisu — pole prostokąta przy obwodzie, pudełko z arkusza, suma kwadratów przy zadanej sumie, funkcja kwadratowa na jawnym przedziale domkniętym. Wszystkie punkty stacjonarne i brzegi/granice. Rozróżnienie optimum, nieosiąganego kresu i nieograniczoności. Istniejący SymPyBridge potwierdza pochodną i pierwiastki pochodnej; to sprawdzenie tą samą biblioteką, nie niezależny dowód całej interpretacji.

## Przykłady

Całka: `x^2`, tryb oznaczony, od `0` do `3` → `9`.

Macierz: `[[1,2],[3,4]]`, wyznacznik → `-2`; odwrotność sprawdzana przez A*inv(A)=I.

Logika: `F AND U` → `F`, `T OR U` → `T`, `U EQUIV U` → `U` w silnej logice Kleene’a.

Zadanie: „Prostokąt ma obwód 40 cm. Wyznacz największe pole.” → boki 10 cm, pole 100 cm². Najmniejsze pole nie istnieje przy dodatnich bokach; kres dolny wynosi 0.

Zadanie: „Funkcja celu f(x) = x^2 - 6*x + 13. Wyznacz minimum na przedziale domkniętym od 0 do 10.” → minimum 4 dla x=3.

## Ograniczenia i ochrona

Kontrolowana gramatyka zadań; nie dowolna treść akademicka. Wyrażenia całek parsowane przez dozwolone węzły AST, bez eval ani sympify surowych danych. Limit obliczenia API: 15 sekund, macierze i wyrażenia ograniczone rozmiarem. Nie dodano treningu, całek wielokrotnych, nieskończonych granic ani dowodzenia twierdzeń. Chronione pliki oraz aktywny checkpoint sprawdzane SHA-256. Kod pozostaje lokalnie; repo publiczne jest dokumentacyjne.


Weryfikacja końcowa: **258 testów matematycznych i regresyjnych + 3 testy komunikacji procesów = 261/261**. Sprawdzono formularze całki oznaczonej, odwrotności macierzy, tabelę Kleene’a i optymalizację w przeglądarce; układ komputerowy i mobilny. Naprawiono kodowanie polskich znaków odpowiedzi na Windows oraz zamknięto poprzednią instancję serwera matematycznego. 11 chronionych plików i aktywny checkpoint bez zmian SHA-256. Wyniki: `docs/AKADEMICKIE_VERIFICATION.json`, dwa raporty XML.
