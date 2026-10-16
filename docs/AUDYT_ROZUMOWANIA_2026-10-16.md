# Audyt rozwiązania i kontrprzykłady — 16.10.2026

Nowa pozycja wspólnego menu: **Audyt rozwiązania i kontrprzykłady**. To deterministyczny audyt narzędziowy oparty na SymPy, bez nowego treningu TSI.

## Dwa tryby

1. **Równoważność kroków:** 2–10 równań, każde w osobnym wierszu. Porównanie zbiorów rozwiązań sąsiednich równań. Wskazanie pierwszego obalonego przejścia, rozwiązań utraconych/dodanych i kontrprzykładu, jeśli został znaleziony. Po błędnym kroku dalsze porównania dotyczą nadal kolejnych par; ich poprawność nie naprawia wcześniejszego błędu.
2. **Tożsamość:** jedna równość i wybrana dziedzina. Symboliczne potwierdzenie lub dokładny kontrprzykład; jeśli nie wystarczają, wynik nierozstrzygnięty.

Oceny: **potwierdzone**, **obalone**, **nierozstrzygnięte**. Nie są to prawdopodobieństwa ani odpowiedzi uczonej sieci logicznej. Brak kontrprzykładu w skończonej próbce nie stanowi dowodu. Potwierdzenie równości zbiorów rozwiązań nie dowodzi prawdziwości modelu wyprowadzonego z dowolnej treści zadania.

## Założenia i zachowanie dziedziny

Jedna zmienna x; dziedzina: rzeczywista, dodatnia, nieujemna albo bez zera. Parser zachowuje ograniczenia oryginalnych operacji przed ich symbolicznym uproszczeniem. Dzięki temu skrócenie `(x-1)/(x-1)` do `1` nie usuwa pamięci wykluczenia x=1.

Dokładne porównanie zbiorów obejmuje równania wymierne z wielomianem licznika stopnia do 6 po uproszczeniu. Funkcje sqrt, Abs, sin, cos, exp, log mogą służyć do kontrprzykładów i potwierdzania tożsamości; ogólne równania z tymi funkcjami mogą pozostać nierozstrzygnięte. Obliczenia mają dotychczasowy limit API 15 sekund. Obsługiwana składnia jest ograniczona, bez dowolnych wywołań kodu.

## Przykłady

| Przejście lub tożsamość | Ocena i przyczyna |
|---|---|
| `x*(x-1)=0` → `x-1=0` | Obalone: utrata x=0 |
| `x=1` → `x^2=1`, x rzeczywiste | Obalone: dodane x=−1 |
| To samo przejście przy x>0 | Potwierdzone |
| `(x-1)/(x-1)=1` → `1=1` | Obalone: drugi zapis wprowadza x=1, gdzie pierwszy jest nieokreślony |
| `2*x+4=10` → `x+2=5` → `x=3` | Potwierdzone |
| `sqrt(x^2)=x`, x rzeczywiste | Obalone, np. x=−1: lewa 1, prawa −1 |
| Ta sama tożsamość przy x≥0 | Potwierdzone |
| `sin(x)=0` → `sin(2*x)=0` | W tym etapie nierozstrzygnięte; nie jest to deklaracja równoważności |

## Raport i zakres

Przycisk **Pobierz raport JSON** zapisuje lokalnie wejściowe kroki i założenia, wyniki, dziedziny, zbiory rozwiązań, kontrprzykłady, wersję SymPy i sumę SHA-256 źródła audytora. Raport nie jest certyfikatem formalnego asystenta dowodów. Brak nowych mechanizmów pamięci profilu użytkownika czy samouczenia na jego błędach. Sprawdzanie dowolnych dowodów, nierówności, układów wielu zmiennych i swobodnej treści pozostaje poza tym etapem.

Dodatek interfejsu: wyniki obliczeń mają równoległy zapis matematyczny i techniczny do skopiowania, np. `x³/3 + C` oraz `x**3/3 + C`; wykresy całek pozostają dostępne.


## Weryfikacja

Pełny zestaw **326/326 testów**, w tym 37 testów audytora: utrata i dodanie pierwiastków, zachowanie dziedziny po skracaniu, założenia, tożsamości, wynik nierozstrzygnięty, kontrola wejścia i rodzina wariantów liczbowych. Dodatkowo po dodaniu metadanych raportu powtórzono 37 testów audytora. Przeglądarka: wybór trybu przez menu, przykłady utraty/dodania, kontrprzykład tożsamości, wynik nierozstrzygnięty, pobranie JSON, widok mobilny i zachowanie wcześniejszej całki z dwoma zapisami i wykresem. 11 chronionych plików oraz aktywny checkpoint bez zmian SHA-256.
