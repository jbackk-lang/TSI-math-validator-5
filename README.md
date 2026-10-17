# TSI-math-validator-5

**Stan aktualny: 17 października 2026.** Lokalny warsztat matematyczny: odczytuje wybrane polecenia, buduje model zadania, oblicza wynik i pokazuje sprawdzenie. Interfejs łączy uczone czytniki TSI, kontrolowane reguły i dokładne obliczenia SymPy.

## Co obecnie potrafi

| Dział | Zakres |
|---|---|
| Równania i wykresy | Pierwiastki, podstawienie sprawdzające, wykres funkcji |
| Zadania tekstowe | Wybrane relacje dwóch liczb, procenty i bilanse, liczebności, ciągi z warunkami, kąty, bryły; pokazuje dane, niewiadome, relacje i cel |
| Optymalizacja | Pole prostokąta, pudełko z arkusza, suma kwadratów, funkcja kwadratowa na przedziale oraz wybrany model prostopadłościanu; dziedzina i osiągalność ekstremum |
| Geometria | Podstawowe pojęcia, części i własności figur, kąty, obwód, pole, jednostki i podstawy trygonometrii w kontrolowanych ćwiczeniach |
| Matryce wielkości | 20 modeli, wybór niewiadomej, zgodne jednostki fizyczne i chemiczne, równania i zależności |
| Całki | Oznaczone na skończonym ciągłym przedziale i nieoznaczone ze sprawdzeniem pochodną; wykres, gdy można go wyznaczyć |
| Macierze | Do 6 × 6: działania, wyznacznik, odwrotność, rząd i układy równań |
| Logika | Klasyczna i trójstanowa Kleene’a |
| Audyt i zapis | Porównanie kolejnych równań, utracone lub dodane rozwiązania, kontrprzykłady; wskazanie miejsca błędu składni i podpowiedź |
| Nauka z poprawek | Bank potwierdzonych lekcji; kontrolowany trening dodatkowego czytnika działań, osobny sprawdzian i możliwość cofnięcia |

Dashboard ma przyciski do podstron, rozwijane menu zadań, wspólne tła paneli i wyrównane przykłady. Na telefonie układ przechodzi w jedną kolumnę. Zapisy `^` i `**` są obsługiwane równolegle; wyniki pokazują zapis matematyczny i techniczny. Przełącznik PL/EN obejmuje główny warsztat; nowe działy geometrii, matrycy i poprawek pozostają częściowo po polsku. Treści zadań opisowych należy wpisywać po polsku.

## Jak korzystać

1. Uruchom panel i wybierz dział z menu albo przyciskiem podstrony.
2. Wczytaj przykład lub wpisz własne dane i kliknij przycisk obliczenia.
3. Sprawdź odczytane dane i warunki, następnie wynik. Przy prośbie o doprecyzowanie uzupełnij wskazany brak.

| Przykład | Oczekiwany wynik |
|---|---|
| „Dwie liczby mają sumę 13 i iloczyn 40.” | 5 i 8 |
| „Prostokąt ma obwód 40 cm. Wyznacz największe pole.” | 100 cm² |
| Całka `x^2` | `x³/3 + C` ze sprawdzeniem |
| Wyznacznik `[[1,2],[3,4]]` | −2 |
| Logika trójstanowa `F AND U` | F |

## Gdzie i kiedy działa

Aplikacja działa lokalnie na Windows przy uruchomionym serwerze: [otwórz dashboard](http://127.0.0.1:8795/). Adres jest dostępny na tym komputerze podczas pracy serwera. GitHub przechowuje dokumentację, nie uruchomioną aplikację.

| Miejsce | Zawartość / uruchomienie |
|---|---|
| `C:\Users\jback\Downloads\a\TSI-math-validator-5` | Lokalne repo z kodem i modelami; `Uruchom_panel_TSI.bat` |
| `C:\Users\jback\Downloads\a\TSI-math-validator-5-Portable` | Wersja Windows x64 z kodem, modelami, Pythonem i bibliotekami; `START.bat`, zatrzymanie `ZATRZYMAJ.bat` |
| `C:\Users\jback\Downloads\a\TSI-math-validator-5-Portable-Windows-x64.zip` | Archiwum portable; rozpakuj w całości przed uruchomieniem |
| [Repozytorium GitHub](https://github.com/jbackk-lang/TSI-math-validator-5) | Dokumentacja i obrazy; bez kodu, wag i danych treningowych |

Portable nie wymaga instalowania Pythona ani pobierania modeli. Prywatny bank lekcji użytkownika nie jest dołączony. Kod źródłowy i paczka z kodem pozostają lokalnie.

## Aktualna weryfikacja i ograniczenia

**948 testów regresji przeszło.** Wybrana próbka znanych zadań CKE/ZPE: **10/10**; nowe warianty tej próbki: **50/50**. To sprawdzenie określonego zakresu, nie całej matematyki.

W szerszym zestawie ZPE obejmującym 204 wpisy i warianty: **15 odpowiedzi kompletnych, 4 częściowe, 185 nierozwiązanych**. Osobny nowy sprawdzian własności figur i słów „każdy”, „może”, „musi”: **2/30**, bez błędnych zaakceptowanych odpowiedzi; sześć kontroli brakujących danych zatrzymano poprawnie. Ten zakres wymaga dalszej rozbudowy.

TSI nie rozumie jeszcze dowolnego opisu. Nierozpoznany warunek, brak ilustracji lub utracony układ tabeli mogą zatrzymać zadanie. Poprawny rachunek nie gwarantuje poprawnego odczytu tekstu. Niewykonany rysunek oznacza wykonanie częściowe. Audyt obejmuje jedną zmienną i wybrane równania wymierne do stopnia 6; nie jest ogólnym narzędziem dowodzenia. Całki niewłaściwe i nieskończone granice są poza potwierdzonym zakresem.

Uczenie podczas użytkowania wymaga potwierdzonych poprawek i przejścia osobnego sprawdzianu. Nie oznacza samodzielnego opanowywania dowolnych tematów. Oryginalne modele pozostają zachowane.

[Historia projektu i wcześniejsze etapy](docs/HISTORIA_PROJEKTU.md) · [Szczegółowa diagnoza ZPE](docs/DIAGNOZA_ZPE_2026-10-17.md)
