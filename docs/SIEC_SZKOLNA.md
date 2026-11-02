# Uruchomienie TSI w sali lekcyjnej — krok po kroku

**Jeden komputer jest serwerem. Uczniowie otwierają jego adres w przeglądarkach.** Materiały, konta i postępy są przechowywane na serwerze. Internet nie jest potrzebny do pracy w szkolnej sieci lokalnej. Identyfikator stanowiska i login ucznia są oddzielne.

## 1. Wybierz komputer nauczyciela / serwer

Pozostaw go włączonego przez całą lekcję. Wszystkie stanowiska muszą mieć dostęp do tej samej szkolnej sieci. Na tym komputerze rozpakuj cały program do jednego folderu. Nie uruchamiaj aplikacji bezpośrednio z ZIP.

Najpierw uruchom zwykłą wersję lokalną przez `URUCHOM.bat`. Otwórz panel nauczyciela i ustaw własne hasło / klucz nauczyciela, jeżeli nie został jeszcze ustawiony. Następnie utwórz konta uczniów, przypisz klasy i dopuszczone poziomy.

Po tej konfiguracji zatrzymaj zwykły lokalny serwer, zanim uruchomisz serwer klasy. Oba tryby domyślnie używają portu **8795**. Nie uruchamiaj równocześnie dwóch kopii na tym samym porcie i folderze danych.

## 2. Ustal adres, który wpiszą uczniowie

Na komputerze serwera otwórz **Wiersz polecenia**, wpisz `ipconfig` i naciśnij Enter. Odczytaj **Adres IPv4** przy aktywnym połączeniu Ethernet lub Wi-Fi. Nie wybieraj karty odłączonej ani wirtualnego adaptera.

Przykład: jeżeli adres serwera wynosi `192.168.1.10`, adresem aplikacji będzie:

```text
https://192.168.1.10:8795
```

**To przykład — zastąp go rzeczywistym adresem swojego serwera.** Administrator powinien zapewnić stały adres lub rezerwację DHCP, żeby nie zmieniał się między lekcjami.

Jeśli szkoła ma własną nazwę DNS dla serwera, można zamiast IP użyć np.:

```text
https://tsi.szkola.local:8795
```

Ta nazwa również jest przykładem. Musi być skonfigurowana w szkolnej sieci. **Nie podawaj uczniom `localhost`, `127.0.0.1` ani `0.0.0.0`** — nie są adresem komputera nauczyciela z perspektywy ich stanowisk.

## 3. Przygotuj certyfikat i klucz serwera

Poproś administratora szkoły o dwa pliki w formacie PEM:

- `serwer-cert.pem` — certyfikat serwera, w razie potrzeby wraz z łańcuchem certyfikatów;
- `serwer-key.pem` — odpowiadający mu klucz prywatny.

Certyfikat musi obejmować **dokładnie tę nazwę lub adres IP**, który wybrano w kroku 2, i być zaufany na komputerach uczniów. Samo przemianowanie pliku na `.pem` nie zmienia jego formatu. Nie pomijaj ostrzeżeń przeglądarki o niewłaściwym lub niezaufanym certyfikacie — administrator powinien poprawić konfigurację.

W folderze programu utwórz podfolder `certyfikaty` i umieść w nim te dwa pliki:

```text
folder-programu/
  URUCHOM_KLASE.bat
  certyfikaty/
    serwer-cert.pem
    serwer-key.pem
```

Klucz prywatny zostaje **wyłącznie na serwerze**. Nie wysyłaj go uczniom, do repozytorium ani do rozmowy z AI. Jeśli certyfikat wymaga zaufania szkolnemu urzędowi certyfikacji, administrator instaluje na stanowiskach jego **publiczny certyfikat**, a nie prywatny klucz serwera.

## 4. Zezwól na połączenia ze szkolnej sieci

Administrator powinien udostępnić port TCP **8795** na serwerze wyłącznie z właściwej sieci szkolnej. Program nie otwiera sam zapory i nie wymaga przekierowania portów do internetu.

## 5. Uruchom `URUCHOM_KLASE.bat`

Dwukrotnie kliknij plik. Program zapyta kolejno o trzy pozycje. Dla przykładowego adresu i folderu z poprzednich kroków wpisz:

| Pytanie w oknie | Przykład wpisu |
|---|---|
| **Adres HTTPS serwera** | `https://192.168.1.10:8795` |
| **Ścieżka certyfikatu PEM** | `certyfikatyserwer-cert.pem` |
| **Ścieżka klucza prywatnego PEM** | `certyfikatyserwer-key.pem` |

Każdy wpis zatwierdź Enterem. Ścieżki względne są liczone od folderu programu. Możesz również podać pełną ścieżkę do rzeczywistego pliku na swoim serwerze.

**W polu klucza podajesz ścieżkę do pliku, nie adres strony, nie jego zawartość i nie hasło nauczyciela.** Nie jest to również klucz API Gemini, OpenAI ani innej usługi. Klucz API nie jest potrzebny do uruchomienia klasy.

Poczekaj na komunikat:

```text
TSI · wspólny serwer klasy: https://192.168.1.10:8795
```

Pozostaw to okno otwarte. Zamknięcie okna serwera lub zatrzymanie go przez Ctrl+C kończy dostęp wszystkich stanowisk. Jeśli uruchomienie zakończyło się błędem, najpierw przeczytaj komunikat — nie uruchamiaj kolejnych kopii.

## 6. Otwórz panel nauczyciela

Na komputerze nauczyciela wpisz w przeglądarce ten sam adres, z końcówką `/nauczyciel`, np.:

```text
https://192.168.1.10:8795/nauczyciel
```

Wpisz hasło / klucz nauczyciela ustawiony w kroku 1. **Hasła nie dopisuj do adresu URL.** Otwórz sekcję „Szafa dydaktyczna i sala lekcyjna”. Znajdziesz tam lekcje, klocki i widok stanowisk. Ten panel jest też dostępny pod obszarem zadania po zalogowaniu nauczyciela.

## 7. Zaloguj uczniów

Na każdym stanowisku otwórz w przeglądarce adres z kroku 2, np. `https://192.168.1.10:8795`. Uczeń wpisuje swój login i hasło. Na stanowisku nie trzeba uruchamiać osobnego serwera ani instalować kopii TSI.

Pierwsze logowanie rozpoczyna wprowadzenie. Konto określa dopuszczony poziom. Stanowisko otrzymuje identyfikator `PC-…`, który pozostaje przy przeglądarce. Adres IP jest informacją pomocniczą, a nie identyfikatorem ucznia. Inna przeglądarka lub usunięcie jej ciasteczek tworzy nowy identyfikator stanowiska.

## 8. Sprawdź stanowiska i postępy

W panelu nauczyciela sekcja „Sala lekcyjna” pokazuje:

- stanowisko oraz aktywność: **●** — ostatni kontakt w ciągu 45 sekund, **○** — starszy kontakt;
- zalogowanego ucznia i klasę;
- aktualny dział i poziom;
- **poprawne odpowiedzi / ocenione próby** oraz liczbę dni nauki;
- czas ostatniej oceny po wskazaniu postępu kursorem.

Widok odświeża się co **15 sekund**. Jest też przycisk „Odśwież postępy”. Aktualizacja nie resetuje pól, gdy nauczyciel właśnie edytuje polecenie dla stanowiska.

W wierszu wybranego stanowiska wybierz dział i poziom, a następnie „Otwórz”. Polecenie dotrze przy kolejnym odświeżeniu stanowiska. Nie obejdzie ograniczenia poziomu przypisanego uczniowi.

Samo otwarcie strony lub wyświetlenie gotowego wyniku nie zwiększa postępu. Brak ocenionych prób nie oznacza niezaliczenia. Jest to podgląd ćwiczeń, nie zabezpieczony system egzaminacyjny.

## 9. Zmień klasę i zakończ lekcję

Uczeń używa „Zmień ucznia / klasę” i wylogowuje się. Kolejny loguje się na swoje konto przy tym samym komputerze. Stanowisko pozostaje to samo, ale postęp i kontekst należą do nowego konta. Niedostarczone polecenie poprzedniego ucznia nie przechodzi na kolejnego.

Serwer może pozostać uruchomiony między lekcjami. Po zakończeniu pracy zatrzymaj go. Kopie danych wykonuj przy zatrzymanym serwerze; konta, wyniki i materiały pozostają w folderze `runtime` na serwerze. Nie publikuj tego folderu, certyfikatów ani prywatnych kluczy.

## Gdy nie działa

| Objaw | Co sprawdzić |
|---|---|
| Zajęty port / program nie startuje | Czy zwykły serwer lub druga kopia klasy nadal działa na 8795 |
| Brak pliku certyfikatu lub klucza | Rzeczywiste nazwy, format PEM, folder `certyfikaty` i wpisane ścieżki |
| Ostrzeżenie certyfikatu | Zgodność nazwy/IP i zaufanie do certyfikatu; poprawia administrator |
| U nauczyciela działa, u ucznia nie | Adres IPv4/DNS, ta sama sieć i reguła zapory dla portu 8795 |
| Niedozwolony adres / Host | Czy użyto dokładnie adresu wpisanego podczas uruchamiania, wraz z portem |
| Brak stanowisk | Czy uczniowie są zalogowani; poczekaj do 15 sekund |
| Brak postępu | Czy uczeń sprawdził własną odpowiedź; samo oglądanie zadania nie jest próbą |
| Nie można wejść na wyższy poziom | Uprawnienia konta ucznia w bazie nauczyciela |

## Stan sprawdzenia

Potwierdzono działanie wspólnego serwera na dwóch niezależnych klientach testowych: osobne stanowiska i postępy, uprawnienia nauczyciela, ograniczenie poziomu oraz potwierdzenie polecenia. Konfiguracja certyfikatu, dostęp między fizycznymi komputerami szkoły i obciążenie całej klasy wymagają odbioru w danej sieci.
