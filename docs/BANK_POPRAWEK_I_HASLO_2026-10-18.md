# Bank poprawek — wycofanie, reset i hasło

Stan: 2026-10-18.

Panel Poprawki TSI jest chroniony hasłem. Przy pierwszym wejściu użytkownik sam ustawia hasło (10–128 znaków). Nie ma hasła fabrycznego. Zapisany jest scrypt z losową solą; hasło nie trafia do repozytorium ani paczki portable. Sesja trwa maksymalnie 30 minut i kończy się po restarcie serwera lub użyciu przycisku Zablokuj panel. Chronione są także administracyjne API, eksport poprawek, odczyt ich pamięci i zapisywanie nowych nazw w słowniku.

## Operacje

- Wycofaj poprawkę: zachowuje wpis w historii ze statusem Wycofane, usuwa jego aktywność w pamięci odpowiedzi i kolejnych zbiorach nauki.
- Reset banku poprawek: wymaga wpisania RESET. Czyści lekcje, sprawdziany, kolejkę oraz pamięć zatwierdzonych poprawek.
- Przywróć kopię: wybór jednej z ostatnich 20 kopii, weryfikacja sum kontrolnych baz i przywrócenie danych banku. Nie włącza dawnego modelu automatycznie.
- Zablokuj panel: unieważnia sesję i wraca do ekranu hasła.

Przed wycofaniem, resetem i przywróceniem powstaje lokalna kopia trzech baz: banku, pamięci i stanu nauki, wraz z manifestem SHA-256. Kopie znajdują się w katalogu runtime/correction_backups. Przywracanie tworzy kolejną kopię stanu sprzed przywrócenia.

Każda z tych operacji wstrzymuje trening, wyłącza aktywną i poprzednią wersję czytnika poprawek i unieważnia bieżące zadanie treningowe. Dzięki temu stary proces nie może później wdrożyć wersji opartej na wycofanej lekcji. Po przejrzeniu danych naukę można wznowić istniejącym przyciskiem.

Reset dotyczy banku poprawek. Nie usuwa słownika pojęć, podstawowych wag, plików programu ani obserwacji diagnostycznych. Ponowne zatwierdzenie wycofanej lekcji wymaga jawnego podania poprawnego wzoru; zachowuje wcześniejszy przydział do lekcji lub sprawdzianu.

Sprawdzenie: 11 nowych testów ochrony i zarządzania bankiem, 41 wcześniejszych testów pamięci/banku/nauki. Wszystkie operacje resetowania w testach wykonano na izolowanych danych syntetycznych. Rzeczywisty bank użytkownika nie został zresetowany ani nie ustawiono za niego hasła.

## Podgląd obwodu i pola

W Geometrii, etap 5, dodano automatyczny podgląd wielokąta z bieżących współrzędnych. Pokazuje wierzchołki i przybliżone długości boków, zachowuje jednakową skalę osi i odświeża się przy zmianie przykładu lub współrzędnych. Dokładne pole, obwód i kontrolę poprawności figury nadal uruchamia przycisk obliczenia. Podpisy obsługują PL/EN.
