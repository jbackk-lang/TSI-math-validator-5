# TSI → układ liniowy → symulowany VQLS

Stan: 2026-10-18. Lokalny prototyp badawczy, bez QPU.

## Co działa

W obecnej stronie Zadania tekstowe znajduje się sekcja „Porównanie solverów — VQLS na symulatorze”. Można wczytać przykład liniowy, porównać bieżące zadanie lub wpisać jawne równania i niewiadome. Wynik pokazuje A, b, rzędy macierzy, dokładne rozwiązanie, przybliżenie wariacyjne, uwarunkowanie i reszty. Eksperyment można zapisać jako JSON z wejściem, wynikiem, parametrami obwodu i sumą kontrolną implementacji.

1. Istniejący czytnik buduje równania albo użytkownik wpisuje je jawnie.
2. Parser oparty na AST sprawdza zapis. Nie wykonuje kodu z wejścia.
3. Kontrola liniowości nie pozwala zastępować x·y niezależną zmienną ani pomijać ograniczeń mianownika.
4. Z liniowego układu powstają dokładne A i b oraz osobny wynik klasyczny.
5. Idealny symulator przygotowuje stan za pomocą trzech warstw RY; przy dwóch kubitach stosuje naprzemienne CNOT. Układy 3×3 są dopełniane do 4×4, 1×1 do 2×2.
6. BFGS minimalizuje globalny koszt 1 − |⟨b̂|A|ψ(θ)⟩|² / ||A|ψ(θ)⟩||². Do czterech deterministycznych startów; optymalizator nie otrzymuje rozwiązania klasycznego.
7. Skala wektora jest odzyskiwana metodą najmniejszych kwadratów z Aψ i b. Dostępne są pełne amplitudy symulatora. To NIE jest odzysk wyniku z pomiarów.
8. Weryfikacja sprawdza pierwotne równania, względną resztę, zgodność z dokładnym rozwiązaniem i — dla zadań tekstowych — potwierdzenie dziedziny przez czytnik. Akceptacja wymaga błędu względnego i reszty ≤ 10⁻⁶.

## Granice prototypu

- Od 1 do 4 rzeczywistych niewiadomych, układ kwadratowy o pełnym rzędzie, współczynniki wymierne.
- Nieliniowości, zmienne w mianownikach, układy prostokątne, sprzeczności, osobliwości i κ(A)>10000 są jawnie zatrzymywane. b=0 ma osobną odpowiedź klasyczną; nie tworzymy zerowego stanu kwantowego.
- Koszt jest liczony przez klasyczne mnożenie macierzy i idealny wektor stanu. Brak implementacji obwodów pomiaru kosztu, kodowania operatora na urządzenie, szumu i shotów.
- Brak QPU, BCOW i Carlemana. Nie zmieniono rdzenia neuronowego ani domyślnego solvera zadań.
- To nie jest demonstracja przewagi kwantowej. Czasy w raporcie obejmują odrębne fragmenty obliczeń, nie kompletny koszt sprzętowego pipeline’u. Pełny odczyt wektora byłby dodatkowym kosztem na QPU.
- Nie każdy opis jest rozpoznawany przez czytnik. Wtedy można użyć jawnych równań; moduł nie zgaduje interpretacji.

## Pierwszy rzeczywisty test lokalny

„Dwie liczby mają sumę 13. Pierwsza jest o 3 większa od drugiej.”

```
A = [[1, 1], [1, -1]]
b = [13, 3]
x = 8, y = 5
```

Względna reszta VQLS: około 7,615·10⁻⁹; 1 symulowany kubit, 141 ocen kosztu. W pierwszym przebiegu fragment klasyczny trwał około 0,00088 s, wariacyjny około 0,0777 s. Wynik jest poprawny, solver klasyczny był szybszy. Liczby są obserwacją tego przebiegu, nie stabilnym benchmarkiem.

Kontrola negatywna: „Dwie liczby mają sumę 13 i iloczyn 40” → wykrycie x·y i odmowa VQLS. Dotychczasowy solver nieliniowy pozostaje dostępny.

24 testy: rozpoznana treść, kontrola nieliniowa, rozmiary 1–4, dopełnianie skalowaną tożsamością (także przy małych współczynnikach), współczynniki niesymetryczne, wyniki ujemne, rząd i sprzeczności, b=0, złe uwarunkowanie, bezpieczeństwo parsera, normalizacja i splątanie obwodu, jawna odmowa przy braku zbieżności. Sprawdzono też endpoint HTTP i interfejs oraz własny Python portable.

## Źródło metody

Bravo-Prieto i in., [Variational Quantum Linear Solver](https://arxiv.org/abs/1909.05820), Quantum 7, 1188 (2023). Prototyp korzysta z koncepcji globalnego kosztu i wariacyjnego przygotowania stanu; nie odtwarza pełnej realizacji sprzętowej publikacji.

Kolejny etap wymaga osobnego eksperymentu: jawne kodowanie A i |b⟩, obwody estymacji kosztu, pomiary i szum. BCOW i Carleman wymagają najpierw zdefiniowania konkretnego modelu dynamiki oraz kontroli błędu.
