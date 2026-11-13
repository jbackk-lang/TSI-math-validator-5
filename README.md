# TSI Math Validator 5

**Wersja 1.3 · 13 listopada 2026 · Windows x64**

TSI Math Validator to lokalny warsztat matematyczny dla uczniów, studentów i nauczycieli. Można w nim rozwiązać zadanie, obejrzeć wykres lub rysunek i sprawdzić własne kroki. Asystent TSI pomaga odczytać dane, uzupełnić brakującą informację i wyjaśnić obliczenie.

## Co jest w środku

| Dział | Do czego służy |
|---|---|
| Równania i funkcje | Rozwiązuj równania, rysuj wykresy i analizuj własności funkcji. |
| Zadania tekstowe | Przejdź od danych i niewiadomych do modelu matematycznego. |
| Geometria | Zacznij od trójkątów i przejdź do kątów, obwodów, pól i brył. |
| Jednostki i matryca | Przeliczaj jednostki, obliczaj koszty i rabaty oraz rozpisuj kolejność działań. |
| Akademickie | Obliczaj całki, wykonuj działania na macierzach, pracuj z logiką i sprawdzaj przekształcenia. |
| Słownik | Wyszukuj terminy matematyczne po polsku i angielsku oraz przeglądaj przykłady. |

Interfejs PL/EN oferuje 15 poziomów widoku, od podstawówki po studia. Nauczyciel może zarządzać zadaniami, materiałami i kontami uczniów oraz przeglądać postępy. Opcjonalny tryb klasy działa w sieci szkolnej po konfiguracji administratora. [Instrukcja serwera klasy](docs/SIEC_SZKOLNA.md)

## Demo i pełne wydanie

| Wydanie | Gdzie w zestawie 1.3 | Rozmiar | Jak zacząć |
|---|---|---:|---|
| Demo | `Demo/Walidator` | ok. 3 KB | Otwórz `START.html` w przeglądarce. Wypróbujesz równanie kwadratowe i obliczenie ceny po rabacie. |
| Pełne | `Pełne/Walidator` | ok. 4,57 GB (4,25 GiB) | Skopiuj cały folder na dysk lokalny, najlepiej SSD, i uruchom `START.bat`. |

Rozmiary dotyczą plików w folderach wydania 1.3. Pełna paczka zawiera Pythona i modele. Panel otwiera się w przeglądarce na stronie **Start**. Kliknij figurę, aby przejść do działu. Po zakończeniu pracy serwer można zatrzymać przez `ZATRZYMAJ.bat`.

## Sprzęt i środowisko

- **System:** Windows x64. Do panelu wystarczy aktualna przeglądarka z JavaScriptem.
- **Procesor:** uruchomienie sprawdzono na Intel Core i5-3470T. Podstawowe obliczenia i sprawdzony dialog działają na CPU.
- **RAM i dysk:** jako praktyczny punkt wyjścia przyjmij **8 GB RAM**, SSD i **co najmniej 6 GB wolnego miejsca**. To zalecenie z zapasem na dane użytkownika. Formalnego minimum RAM ani wydajności przy obciążeniu całej klasy jeszcze nie zmierzono.
- **Internet:** podstawowe obliczenia i lokalny panel działają na komputerze użytkownika. Wyszukiwanie online i zewnętrzne usługi AI wymagają połączenia.

## Co zmieniło się w 1.3

- Nowa strona Start z powitaniem i figurami prowadzącymi do działów.
- Uporządkowany panel geometrii i podpowiedzi dopasowane do zakupów oraz rabatów w dziale Jednostki.
- TSI zachowuje długości boków w rozmowie o polu trójkąta, dopytuje o kąt i korzysta z odpowiedzi w kolejnym kroku. W pełnej paczce sprawdzono przez serwer panelu przypadek 7 cm, 9 cm i 30°, z wynikiem **15,75 cm²**.

## Dostępność

Powyższa tabela opisuje zestaw lokalny 1.3. Na GitHubie dostępne jest osobne, wcześniejsze demo Windows x64. [Publiczne wydania na GitHubie](https://github.com/jbackk-lang/TSI-math-validator-5/releases)

[Archiwalny opis i wcześniejsze wydania](docs/README-wydania-do-2026-11-04.md)
