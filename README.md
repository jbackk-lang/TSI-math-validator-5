# TSI-math-validator-5

**Stan: 24 października 2026.** Lokalny warsztat matematyki: obliczenia, rysunki, sprawdzanie rozwiązań i nauka z wirtualnym asystentem TSI.

## Pobierz demo — Windows x64

[Pobierz paczkę ZIP](https://github.com/jbackk-lang/TSI-math-validator-5/releases/download/v2026.10.24-demo.1/TSI-Math-Validator-DEMO-Windows-x64-2026-10-24.zip) · [Wydanie i suma SHA-256](https://github.com/jbackk-lang/TSI-math-validator-5/releases/tag/v2026.10.24-demo.1)

**Rozmiar:** 17,34 MB ZIP; około 57,01 MB po rozpakowaniu (MB = 1 000 000 bajtów).

Rozpakuj **cały katalog**, uruchom **URUCHOM.bat** i pozostaw okno serwera otwarte. **ZAMKNIJ.bat** zamyka tę instancję demo. Własny Python jest dołączony; obliczenia nie wymagają instalacji, internetu ani klucza API.

**Demo:** równania i wykresy, analiza funkcji i całek, macierze, logika, audyt, jednostki, jawne modele wielkości, geometria i bryły, kąty trójkąta, podstawowe modele fizyczne oraz słownik. Obliczenia korzystają z SymPy i mpmath.

**Pełna wersja lokalna:** dodatkowo model TSI, rozmowa i kontekst, czytniki opisów, pamięć, trening, panel edycji nauczyciela i import OCR. Tych funkcji modelu i ich kodu nie publikujemy w demo. Niektóre odnośniki demo pokazują informację o funkcji pełnej wersji.

## Możliwości pełnej wersji lokalnej

| Dział | Możliwości |
|---|---|
| Start | Menu „co, gdzie i jak”; poziom podstawowy, licealny i akademicki |
| Wirtualny asystent | Wyskakujące okienko **Zapytaj TSI**; pomocnik, nauczyciel, narrator; kontekst bieżącego zadania i klikniętej wielkości |
| Figury i bryły | 19 modeli, podstawy nazw i części, obwody, pola, powierzchnie, objętości, jednostki i rysunki |
| Trójkąty i kąty | Trzeci kąt, trójkąt równoramienny, równoboczny i prostokątny, kąty zewnętrzne, cosinusy i wektory; wskazówki oraz własne odpowiedzi |
| Równania i funkcje | Rozwiązania, dziedzina, pochodne, zera, ekstrema, asymptoty i wykresy w obsługiwanym zakresie |
| Całki | Oznaczone i nieoznaczone, wykresy, pierwotna, kontrola pochodną, dziedzina, osobliwości, pole ze znakiem i geometryczne; π, e, `^` i `**` |
| Zadania tekstowe | Dane, niewiadome, zależności i rysunki dla rozpoznanych konstrukcji; lekcje kątów także na stronie zadań |
| Fizyka | Dział dostępny z każdego panelu; w menu poziomów od liceum, z wprowadzeniem do wielkości i jednostek; cztery modele mechaniki pręta |
| Pozostałe narzędzia | Macierze, logika klasyczna i T/F/U, audyt kroków, korekta wzorów z dokumentów i obrazów, mini klawiatura matematyczna |
| Nauczyciel | Bank zadań według działu i poziomu: dodawanie, edycja, wycofanie i przywracanie; razem z poprawkami i uczeniem TSI, **pod hasłem** |
| Nauka ucznia | Wspólna oprawa **Nauka · Ocena · Powtórki**, lokalna historia prób, pogrubione odpowiedzi i przekreślenie potwierdzonych błędów |

Główne menu ma wspólną kolejność i wygląd we wszystkich działach. **Jednostki** prowadzą do przelicznika i zależności wielkości; **Matryca** do rozpisywania działań. Przełączanie tematu odświeża właściwy formularz.

Przy zmianie figury etap nauki dopasowuje się do jej tematu. Kliknięcie wymiaru zawęża pomoc do tej wielkości; „Całe zadanie” przywraca pełny zakres. Zmiana danych unieważnia wcześniejsze obliczenie w kontekście asystenta.

## Jak zacząć

Uruchom lokalny panel i otwórz **`http://127.0.0.1:8795/start`**. Wybierz dział, poziom i tryb Obliczenia / Wiadomości / Nauka. Przyciskiem **Zapytaj TSI** otworzysz asystenta. **Nauczyciel** prowadzi do chronionej konsoli; używa dotychczasowego hasła panelu poprawek.

| Przykład | Wynik lub działanie |
|---|---|
| `Policz kąt trójkąta` | TSI pyta o dane |
| Następnie `40 i 60` | Trzeci kąt: **80°** |
| Prostokąt, boki 4 cm i 3 cm | Pole: **12 cm²** |
| `x^2 - 64 = 0` | **−8 i 8** |
| Całka z `x^2` od 0 do 3 | **9** |
| Kliknięcie α=40° i „Wyjaśnij” | Pomoc dotycząca wybranego kąta |

## Sprawdzenia i stan TSI

Lekcje i bank nauczyciela: **36/36** kontroli. Integracja działającej aplikacji: **20/20**. Działający wirtualny asystent i jego kontekst: **12/12**. [Dokładny zakres](docs/WIRTUALNY_ASYSTENT_I_NAUCZYCIEL_2026-10-24.md).

Wagi działającego TSI zachowano. Ostatni udokumentowany moduł dowodowy: **10 227 859 parametrów**, **41,28 MB** pliku wag — to jeden składnik aplikacji, nie całe portable. Swobodna rozmowa nie osiągnęła wymaganego poziomu. Opcjonalny dostęp przez OpenAI API jest podłączony w pełnej wersji lokalnej; wymaga własnego klucza i wybranego modelu. Połączenie z płatnym modelem nie było testowane na rzeczywistym kluczu.

Pełna wersja z modelem TSI pozostaje lokalna. Publiczne demo zawiera narzędzia matematyczne i własne środowisko uruchomieniowe, bez kodu sieci, wag i treningu TSI.

[Zakres demo i sprawdzenia](docs/DEMO_2026-10-24.md)

## Podgląd

![Demo — wspólne menu i jednostki](docs/demo-menu.png)

![Start — poziom licealny](docs/welcome-secondary.png)

![Wirtualny asystent — pomoc do wybranego kąta](docs/virtual-assistant-triangle.png)

[Przebieg prac i ograniczenia zakresu](docs/WIRTUALNY_ASYSTENT_I_NAUCZYCIEL_2026-10-24.md) · [README sprzed przebudowy](docs/archiwum/README_before_virtual_assistant_2026-10-24.md) · [Wcześniejsza integracja pamięci](docs/PAMIEC_TSI_2026-10-24.md)
