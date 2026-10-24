# Podłączenie rozmowy i pamięci TSI — 24 października 2026

MUZ i walidator korzystają teraz z usługi rozmowy działającej instalacji TSI oraz inkubatora źródeł. Rozmowa nie wymaga uruchomienia osobnego serwera TSI: aplikacja uruchamia lokalny proces przez istniejącą konfigurację wspólnej instalacji. Ten etap nie instaluje dużego modelu badawczego ani nowych wag.

Każda aplikacja ma własną bazę rozmów i inkubatora. Profil przeglądarki jest nadawany po stronie serwera; użytkownik innego profilu nie otrzymuje jego zapisów. Nowa rozmowa zachowuje pamięć. Zapisane wypowiedzi użytkownika nie stają się automatycznie potwierdzonymi faktami o świecie. Przy niepełnym odczycie możliwe jest przywołanie dokładnego źródła.

Na stronach dodano rozwijany panel **TSI · rozmowa i pamięć**. Zawiera polecenia PL/EN, wysyłanie Enterem, nową rozmowę, przegląd źródeł, wybór i zamykanie tematów, pauzę pamięci, zatwierdzanie i odrzucanie informacji oraz cofnięcie jednej lub dwóch decyzji. Dane widoczne jako źródło nie są wykonywanymi poleceniami.

Bufor początkowy: 10 000 wpisów / 64 MiB treści; wzrost do 200 000 / 1 GiB treści. Fizyczny rozmiar bazy obejmuje dodatkowo indeksy. Nie jest to nowy pomiar rozmiaru portable. W ramach tego etapu zaktualizowano katalogi robocze; paczek ZIP i osobnych rozpakowanych portable nie przebudowano.

## Wyniki sprawdzianów

| Zakres | Wynik |
|---|---:|
| Przygotowane połączenie MUZ: pamięć po nowej rozmowie i restarcie procesu, profile, dodawanie, pauza | 5/5 |
| Przygotowane połączenie walidatora: te same kontrole | 5/5 |
| Działający MUZ: panel, pamięć, dodawanie, zarządzanie pamięcią, tabela budżetu, odrzucenie obcego pochodzenia | 6/6 |
| Działający walidator: panel, pamięć, dodawanie, zarządzanie pamięcią, wyznacznik macierzy, odrzucenie obcego pochodzenia | 6/6 |

Próby używały osobnych przykładowych profili: różne kolory plecaka w obu aplikacjach. Nie modyfikowano rachunków ani danych użytkownika. Test tabeli MUZ sprawdził odpowiedź interfejsu danych, nie kompletny plan oszczędnościowy. Test akademicki sprawdził wyznacznik macierzy 2 × 2; nie stanowi sprawdzianu wszystkich tematów.

## Rola nauczyciela i zarządcy

Istniejące obliczenia, geometria, całki i funkcje budżetowe nadal wykonują swoje zadania. Nowy panel rozmowy jest połączony z TSI, ale nie przejmuje automatycznie wszystkich bieżących danych formularzy i finansów. Nie należy zakładać, że pytanie w panelu odwołuje się do aktualnego rysunku bez przekazania jego danych.

Kolejnym etapem dla walidatora jest rozmowa nauczycielska powiązana z aktualnym zadaniem: wskazówki bez zdradzania wyniku, kontrola kroków, wyjaśnienia oraz dobór powtórek. Dla MUZ: rozmowa powiązana z wybranym planem i jawnym stanem budżetu. Swobodna rozmowa TSI nie osiągnęła wymaganego poziomu. Zwykłe używanie pamięci nie trenuje wag; internetowa pętla treningu pozostaje wyłączona.
