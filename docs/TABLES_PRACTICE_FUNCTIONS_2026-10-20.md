# Tabele tematów, powtórki i funkcje elementarne — 20 października 2026

## Tabele przykładów

Edytowalne przykłady są dostępne w równaniach i wykresach, całkach, macierzach, audycie, logice klasycznej i trójstanowej, matrycy, zadaniach tekstowych, optymalizacji oraz etapach geometrii, w tym trygonometrii.

W tabeli można zmienić nazwę i dane, dodać wiersz, dopisać aktualne dane formularza, wczytać przykład i usunąć wiersz. Przywracanie domyślnych zachowuje własne wpisy. Zapis pozostaje w tej przeglądarce, oddzielnie według tematu; nie jest częścią wag TSI ani plikiem współdzielonym między komputerami. W równaniach limit wynosi 50 wierszy; w pozostałych formularzach 30 na temat. Brak dostępu lub miejsca w pamięci przeglądarki jest zgłaszany.

Dane są dostosowane do narzędzia: wzór i granice całki, macierze A/B z działaniem, kolejne równania audytu, wartości logiczne, opis zadania, współrzędne i jednostki figur. Wczytanie uzupełnia formularz; obliczenie uruchamia użytkownik. W trybach zmieniających zestaw pól najpierw wybierz temat lub model w głównym formularzu. Dotychczasowe skróty i ćwiczenia edukacyjne pozostają dostępne.

![Edytowalne przykłady całek](edytowalne-przyklady.png)

## Powtórki z błędów

Sekcja **Powtórki z moich błędów** znajduje się w analizie równań. Potwierdzona utrata lub dodanie rozwiązania podczas kontroli własnych kroków tworzy wpis do powtórki. Nierozstrzygnięte przejście nie tworzy błędnej lekcji.

**Ćwicz podobny problem** generuje inny wariant liczbowy. W tym etapie ćwiczenia dotyczą utraty rozwiązania przy skracaniu przez czynnik i dodania rozwiązania przy potęgowaniu. Odpowiedź sprawdza audytor symboliczny. Postęp uwzględnia pierwszą ocenioną odpowiedź w danym wariancie; dwie kolejne poprawne pierwsze odpowiedzi na różnych wariantach przesuwają powtórkę o dobę. Można ćwiczyć wcześniej lub usunąć wpis. Postęp przetrwa odświeżenie strony w tej samej przeglądarce. To personalizacja ćwiczeń, bez automatycznej zmiany wag modelu.

## Analiza funkcji elementarnych

Do wielomianów i funkcji wymiernych dołączono `sqrt(x)`, `log(x)`, `exp(x)`, `sin(x)`, `cos(x)`, `tan(x)` oraz obsługiwane kombinacje i równania, np. `sin(x)=cos(x)`. `log` jest logarytmem naturalnym; argumenty funkcji trygonometrycznych są w radianach.

- Dziedzina oryginalnego zapisu jest zachowana także po skróceniu lub redukcji wyrażeń.
- Dziedzina i symboliczny zbiór rozwiązań są podane dla całej osi rzeczywistej.
- Dla funkcji elementarnych widoczne zera, monotoniczność, ekstrema oraz przedziały znaku dotyczą wybranego okna wykresu. Własności wielomianów i funkcji wymiernych pozostają analizowane w ich całej dziedzinie.
- Granice w nieskończoności są obliczane tam, gdzie zostały ustalone. Oscylacyjny zakres nie jest przedstawiany jako istniejąca granica. Asymptoty i przerwy są sprawdzane; wykres nie łączy gałęzi przez wykluczone argumenty.
- Kliknięcie przedziału dodatniości lub ujemności zaznacza go na wykresie.

Ograniczenia tej partii: okno funkcji elementarnych ma najwyżej 100 jednostek szerokości, w zakresie od −1000 do 1000. Argument trygonometrii ma postać `a*x+b`, z |a| ≤ 10. Nierozstrzygnięte własności są oznaczane, zamiast przedstawiania ich jako brak. To nie jest pełny system dowodzenia własności dowolnej funkcji. Gęste lub trudne symbolicznie zadania mogą wymagać zawężenia okna albo uproszczenia zapisu. Widok jest numerycznym podglądem.

## Weryfikacja

- Tabela równań: 8 kontroli obejmujących edycję, zapis po odświeżeniu, wczytanie, nowy wiersz, przywrócenie domyślnych, zachowanie własnych wpisów, usunięcie i angielski.
- Tabele tematów: 18 kontroli obejmujących narzędzia akademickie, zadania tekstowe, optymalizację, matrycę i wszystkie osiem etapów geometrii oraz język angielski.
- Powtórki: 5 kontroli przebiegu w przeglądarce — powstanie z błędu, dokładna ocena odpowiedzi, zmiana liczb, przesunięcie terminu i zachowanie postępu po odświeżeniu.
- Funkcje elementarne: 8 przypadków z kontrolą zer, ekstremów, dziedziny lub asymptot, w tym zachowanie dziedziny po redukcji `sqrt(x)-sqrt(x)+1`.
- Dodatkowe 5 kontroli znaku i ograniczeń, w tym dodatnia funkcja `1/(x^2+1)` na całej osi.
- Przeglądarka funkcji elementarnych: 6 kontroli — pierwiastek, logarytm, sinus, tangens, klikany przedział znaku i angielski.
- Zachowana analiza wcześniejszego zakresu: 27/27 prób. Sprawdziany dotyczą wskazanych przypadków; nie są wynikiem dla całej matematyki.

Wdrożono w lokalnym folderze roboczym. Paczka portable nie została przebudowana w tej partii. Dokumentacja publiczna zawiera opis i obrazy, bez kodu oraz modeli.
