# Trening czytnika akademickiego V2 — 20 października 2026

Model: `TSI-ACADEMIC-INTENT-698483d3`; 263 175 parametrów. Trening: 2448 przykładów, zbiór rozwojowy: 232. Epoka wybrana na podstawie straty rozwojowej: 40. Próg pewności 0,65 wybrano przed sprawdzianem na zbiorze rozwojowym.

Nowy odłożony sprawdzian: **19/24** pełnych poprawnych wykonań, **1 błędne wykonanie** zadania, **0/12** niepożądanych wykonań poleceń odrzuconych. Retencja poprzednich sprawdzanych umiejętności: **8/8**. Narzędzia z prawidłowo podanym celem i danymi: **24/24**.

Warunek wdrożenia: 24/24, bez błędnych wykonań i z retencją 8/8. **Niespełniony — nie wdrożono i nie zmieniono głównego rdzenia.**

V1 i V2 mają różne sprawdziany; 18/24 i 19/24 nie stanowią bezpośredniego pomiaru poprawy. Nowy sprawdzian obejmuje cztery parafrazy dla każdego z sześciu celów; dane liczbowe są wspólne w obrębie celu, zatem zakres jest ograniczony. Wyniki nie mierzą ogólnego rozumienia języka ani jakości wykładu.

## Odczyty sprawdzianu

| Zadanie | Oczekiwany cel | Przewidywany cel | Pewność |
|---|---|---|---|
| derivative-1 | derivative | derivative | 0.975 |
| derivative-2 | derivative | derivative | 0.939 |
| derivative-3 | derivative | derivative | 0.972 |
| derivative-4 | derivative | reject | 0.648 |
| integral-1 | integral | integral | 0.970 |
| integral-2 | integral | integral | 0.998 |
| integral-3 | integral | derivative | 0.787 |
| integral-4 | integral | reject | 0.631 |
| definite-1 | definite | definite | 0.996 |
| definite-2 | definite | definite | 0.996 |
| definite-3 | definite | definite | 0.842 |
| definite-4 | definite | definite | 0.618 |
| equation-1 | equation | equation | 0.999 |
| equation-2 | equation | equation | 0.975 |
| equation-3 | equation | equation | 0.966 |
| equation-4 | equation | reject | 0.941 |
| determinant-1 | determinant | determinant | 0.999 |
| determinant-2 | determinant | determinant | 0.712 |
| determinant-3 | determinant | determinant | 0.994 |
| determinant-4 | determinant | determinant | 0.971 |
| inverse-1 | inverse | inverse | 0.966 |
| inverse-2 | inverse | inverse | 0.984 |
| inverse-3 | inverse | inverse | 0.768 |
| inverse-4 | inverse | inverse | 0.871 |
| reject-1 | reject | reject | 0.800 |
| reject-2 | reject | reject | 0.979 |
| reject-3 | reject | definite | 0.610 |
| reject-4 | reject | reject | 0.476 |
| reject-5 | reject | determinant | 0.633 |
| reject-6 | reject | integral | 0.366 |
| reject-7 | reject | integral | 0.999 |
| reject-8 | reject | equation | 0.995 |
| reject-9 | reject | definite | 0.997 |
| reject-10 | reject | reject | 1.000 |
| reject-11 | reject | derivative | 0.974 |
| reject-12 | reject | definite | 0.999 |
