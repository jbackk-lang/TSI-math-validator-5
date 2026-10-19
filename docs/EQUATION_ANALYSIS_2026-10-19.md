# Analiza równań, import i aktualny TSI — 19 października 2026

W warsztacie Równania i wykresy dodano sekcję **Analiza równania i własności funkcji**.

## Użycie

1. Wpisz wzór lub równanie i wybierz **Analizuj i opisz**. Dla równania badana funkcja to różnica lewej i prawej strony.
2. Zaznacz **Aktualizuj po zmianie**, aby analiza ruszała po zakończeniu edycji. Zmiana danych usuwa nieaktualny opis.
3. Możesz pokazać obie strony równania, pochodną oraz odczytać przybliżone współrzędne kursorem.
4. Rozwiń **Wczytaj równanie ze zdjęcia lub dokumentu**. Wybierz PDF, TXT, MD, DOCX, PNG, JPG lub WEBP do 8 MB. Możesz też wkleić tekst lub zdjęcie ze schowka. W PDF wybierz stronę.
5. Wybierz odczytany wiersz, popraw go w polu **Popraw odczytany wzór** i użyj mini klawiatury. **Zastosuj poprawiony wzór** przenosi go do głównego pola; analiza wymaga uruchomienia.

## Potwierdzony zakres

Wielomiany i funkcje wymierne jednej zmiennej x, z ograniczeniem stopnia do 6 podczas budowania wzoru. Dziedzina oryginalnego zapisu, rzeczywiste zera, sprawdzenie podstawieniem, pochodna, przedziały monotoniczności, izolowane ekstrema lokalne, asymptoty pionowe i wielomianowe, usuwalne nieciągłości. Wykres ma przerwy przy wykluczonych argumentach. Zakres osi y jest przycinany dla czytelności. Opis i obsługa PL/EN.

Przykłady: `x^2-64`, `-x^2+64`, `x^2+1`, `x^3-3*x`, `1/(x-1)`, `(x^2-1)/(x-1)`, `x^2=2*x+3`, `x/x=1`.

Symbole mini klawiatury obejmują także zapisy przydatne w dotychczasowym warsztacie. Obecna pełna analiza wymierna nie obejmuje jeszcze funkcji trygonometrycznych, pierwiastkowych ani logarytmicznych. Nieznany zapis jest zgłaszany zamiast pomijania fragmentu.

## Aktualny czytnik TSI

Zaktualizowano lokalną kopię ogólnego TSI z 19 października: wyuczony czytnik operacji i argumentów, matryce językowe, aktywne moduły i słowniki. Adapter korzysta teraz również z wyuczonego czytnika, zamiast ograniczać wejście do listy początkowych czasowników. Główne wagi H512 mają ten sam identyfikator; nie jest to nowy trening tych wag. Dotychczasowe solvery matematyczne pozostają dostępne.

Opcja **Dodatkowy odczyt kształtu przez TSI** używa modułu TSI-SIGNALS-TURNING-f3792b5d do próbek funkcji na wybranym przedziale. Rozpoznaje kandydatów: trend, skok, impuls, okresowość, zwrot. Nie zastępuje symbolicznej pochodnej i nie rozstrzyga zbieżności całki. Nieciągły przedział nie jest kierowany do tej klasyfikacji. Pierwsze uruchomienie uczonego modułu może trwać dłużej niż analiza symboliczna.

## Dokumenty i OCR

Odczyt lokalny, bez wysyłania dokumentów do usług zewnętrznych. PDF z tekstem: ekstrakcja wybranej strony. Zdjęcia i skany PDF: Windows.Media.Ocr, wymagający dostępnego języka OCR systemu Windows. Odczyt OCR oraz układ wzorów w PDF/DOCX wymagają kontroli; nie gwarantujemy poprawnego rozpoznania pisma odręcznego, piętrowych ułamków ani indeksów. Próba drukowanego `x^2` dała `xA2`, a `0` zostało odczytane jako `O`; temu służy korekta przed analizą. Pusty skan zgłasza brak czytelnego tekstu.

## Sprawdzenie

- 27 prób analizy: przeciwne znaki, brak zer rzeczywistych, równania, tożsamości, sprzeczności, skracanie ułamków, wykluczenia, ułamki dziesiętne i odrzucanie nieobsługiwanych zapisów.
- 42 testy aktualnego czytnika: PL/EN, role, kolejność działań, kontekst, negacje, braki, przekazanie zadania do narzędzi i spójność kopii.
- 8 prób importu: TXT, UTF-8, DOCX, obraz OCR, rzeczywisty PDF egzaminacyjny i niepoprawne wejścia.
- 10 kontroli przeglądarki: analiza, aktualizacja po zmianie, obie strony, pochodna, język, uczony moduł, usuwanie starego wyniku i ekran telefonu.
- 6 kontroli importu w przeglądarce: zdjęcie, podgląd, korekta klawiaturą, rozwiązanie poprawionego wzoru, TXT, PL/EN i układ telefonu.

To weryfikacja tego zakresu, a nie całej matematyki. Kopie poprzednich plików zachowano lokalnie. Ta aktualizacja dotyczy folderu roboczego; archiwum portable nie zostało w tej partii przebudowane.

![Import i korekta równania](import-korekta-rownania.png)
