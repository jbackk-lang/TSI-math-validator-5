# Kontynuacja treningu wspólnej gałęzi TSI — V2, 20 października 2026

Model: `TSI-SHARED-EVIDENCE-bc8e21c9`. Kontynuacja wag `TSI-SHARED-EVIDENCE-e33cfcce`, bez zmiany architektury i bez wymiany głównego H512. 266 907 parametrów.

Trening: 3840 syntetycznych przykładów, zbiór rozwojowy: 480. Wagi wybrano w kroku 350 na podstawie straty rozwojowej. Test był odłożony przed treningiem.

- Nowy, trudniejszy sprawdzian relacji: **960/960**. Poprzednie wagi na tym samym nowym sprawdzianie: **884/960**.
- Poprzedni sprawdzian relacji: **720/720**, wcześniej 713/720.
- Zachowanie oryginalnego T/F/U: **640/640**, wcześniej 640/640.
- Próby zmiany kolejności i nazw: **16/16 grup**, łącznie 48 wariantów, z kontrolą przewidywań samej sieci.
- Dodatkowe próby działania: **24/24**, zgodność sieci z audytem 24/24.

## Poszczególne stany

| Stan | Poprawne | Przypadki |
|---|---:|---:|
| Potwierdzenie | 240 | 240 |
| Zaprzeczenie | 240 | 240 |
| Brak informacji | 240 | 240 |
| Sprzeczność | 240 | 240 |

## Zakres

Testuje jawne, uporządkowane fakty: dopasowanie podmiotu, relacji, wartości i zakresu, polaryzację, braki i sprzeczności. Trening obejmuje wiele powtórzeń zgodnej informacji wobec pojedynczego zaprzeczenia, dane rozpraszające, pusty kontekst i do 64 faktów. Nazwy z obszarów MUZ, matematyki i sygnałów są jedynie etykietami danych; porównania ról przekazuje adapter.

To test relacji w danych syntetycznych, a nie test rozumienia dowolnego tekstu, jakości wykładu, prognozy finansowej lub diagnozy fizycznej. Powtarzające się schematy relacji mogą występować w różnych częściach danych; nie jest to kwalifikacja do pełnego zastąpienia człowieka.

Nowe wagi pozostają wewnętrzną gałęzią `TSISystem.shared_matrix`. Nie zmieniono dotychczasowej metody odpowiedzi rdzenia ani jego wag. Zachowano niezależną kontrolę źródeł i kopię poprzedniej wersji. Nie zaktualizowano paczki ZIP.
