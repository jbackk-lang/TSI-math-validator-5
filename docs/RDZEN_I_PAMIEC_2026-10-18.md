# Aktywny rdzeń i trwała pamięć — 18.10.2026

## Właściwy rdzeń został wymieniony

Aktywna konfiguracja `code/tsi_core/active_system.json` wskazuje nowy checkpoint **H512**. To rozszerzenie właściwej architektury `WordVectorGeometryCore`, a nie tylko osobnego generatora wypowiedzi.

- Szerokość dodatkowego stanu rekurencyjnego: **256 → 512**.
- Parametry rodzimego parsera/rdzenia: **670 250 → 2 054 186**.
- Rdzeń wraz ze współdzieloną pamięcią i logiką: **784 338 → 2 168 274** parametrów.
- Zachowano interfejs wektorów 96D, istniejący moduł pamięci faktów i logiki. Ich dotychczasowy kontrakt danych nie został automatycznie rozszerzony.

Wagi przeniesiono tak, aby nowe jednostki początkowo nie zmieniały wcześniejszego działania. Przeniesiono stan optymalizatora. Poszerzono również odczyt relacji i powiązano moduły zależne z nowym checkpointem. Oryginalne pliki wag pozostały zachowane.

Sprawdzian transferu: **210 poleceń polskich, 210 angielskich, 4096 prób operacji wektorowych i 512 par relacji**. W tych próbach różnica wcześniejszych i nowych wyników wyniosła zero. To test zachowania wcześniejszego działania, nie dowód opanowania nowych zadań.

Raport i kopia konfiguracji poprzedniej wersji są w `code/tsi_core/artifacts/native_growth_512/`. Konfiguracja poprzednia i jej suma kontrolna pozwalają przygotować cofnięcie bez kasowania modeli. Ustawienia nadzorcy treningu dopuszczają następne poszerzenie do H1024: silne pogorszenie wcześniejszej straty uruchamia wzrost od razu, a mniejsze utrzymujące się pogorszenie po trzech oknach pomiaru. Nie jest to ogólne samouczenie w czasie dowolnej rozmowy.

## Pamięć poza wagami

Lokalna baza `runtime/tsi_memory.sqlite` przechowuje osobno:

- jawne znaczenia i formy ze słownika;
- zatwierdzone poprawki przydzielone do ćwiczeń;
- obserwacje błędów, które nie są uznawane za wiedzę;
- historię dodawania, przywołania i rozstrzygania konfliktów.

Dla identycznego polecenia (po normalizacji wielkości liter i odstępów) TSI może przywołać zatwierdzony wzór i ponownie przeliczyć go dokładnym narzędziem. Nie podmienia liczb, nie usuwa negacji i nie uznaje podobnej parafrazy za ten sam opis. To pamięć zatwierdzonej interpretacji, nie nowa umiejętność rozumienia języka.

Dwie różne zatwierdzone interpretacje powodują konflikt i wstrzymanie przywołania do jawnego wyboru użytkownika. Rozstrzygnięcie zachowuje historię. Przykłady odłożone na sprawdzian nie wchodzą do podpowiedzi ani listy powtórek. Niejednoznaczne znaczenia pozostają listą kandydatów.

Testy sprawdziły odczyt poprawki w osobnym procesie Pythona, ponowne otwarcie kopii SQLite, odmowę użycia uszkodzonego wpisu, konflikt oraz wykluczenie sprawdzianów. Zapis jest niezależny od wag modelu. Prywatna baza i jej kopie pozostają lokalnie i nie są dołączane do GitHub ani paczki portable.

## Gdzie tego używać

Nowe działanie jest w istniejących **Zadaniach tekstowych**. Nie dodano kolejnej strony. Pole „Odczyt z kontrolą odpowiedzi” jest domyślnie włączone; można je odznaczyć, by użyć wcześniejszego czytnika opisu. Narzędzia obliczeniowe nadal wykonują dokładne rachunki.

Pełny nowy przepływ obejmuje kontrolowane opisy kwadratu, prostokąta, koła i trójkąta: opis → dane i cel → istniejący solver → odpowiedź większego modułu językowego → sprawdzenie sensu. Zestaw akceptacyjny: 24/24 po poprawkach; kolejny zamrożony sprawdzian: 26/26 w pierwszej próbie. Zestawy są autorskie i małe. Pozostałe wcześniej obsługiwane typy zadań korzystają z odpowiednich istniejących czytników i narzędzi.

Strona **Poprawki TSI** wyjaśnia teraz swój cel: użytkownik zatwierdza poprawną interpretację polecenia, a program ćwiczy na zatwierdzonych danych i sprawdza zmianę. Przykład formularza jedynie wypełnia pola; nie zapisuje danych ani nie uruchamia treningu. Ta strona służy poprawianiu TSI, nie nauczaniu użytkownika. Na niej można też sprawdzić pamięć dla wpisanego polecenia, rozstrzygnąć konflikt i zapisać kopię pamięci.

## Zakres nauki językowej

Większy generator językowy 253 668 parametrów również jest aktywny. To odrębny element od właściwego rdzenia H512. Liczb tych nie należy utożsamiać ani przedstawiać jako rozmiaru całego systemu wraz z innymi modelami, w tym używanym przez menedżer encoderem HerBERT.

Cztery kolejne etapy ćwiczeń z powtórkami — polecenia, geometria, masa/prędkość, objętość/czas — zakończyły się 25/25 zachowanych znaczeń dla każdego z trzech startów. W jednym starcie wystąpił przejściowy spadek 12/12 → 11/12 po pierwszym nowym temacie, a następne etapy wróciły do 12/12. Zapisano całą historię, nie tylko wynik końcowy. Są to powtarzane znane sprawdziany, nie niezależny egzamin ogólnego języka.

Nowy zakres kompetencji musi zostać osobno wyuczony i zweryfikowany. Większa pojemność daje miejsce na dalszą naukę; sam transfer nie dodaje wiedzy. Rysunki, dowolne długie teksty, swobodna rozmowa oraz mówienie głosem nadal wykraczają poza potwierdzony zakres.

## Końcowe sprawdzenie aplikacji

Pełna regresja po wymianie rdzenia: **1982/1982**. Następnie rozszerzono raporty dla nowego przepływu językowego: **22/22**, w tym dwa nowe testy, co daje **1984 różne zaliczone testy**. Zweryfikowano też odczyt syntetycznej poprawki po ponownym uruchomieniu serwera, ten sam identyfikator pamięci i ponowne przeliczenie wyniku. Rzeczywisty raport nowego przepływu został odtworzony przez HTTP.
