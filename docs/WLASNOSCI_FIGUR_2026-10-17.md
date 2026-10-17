# Własności figur i kwantyfikatory — 17.10.2026

## Aktualny wynik

Poprzednie 2/30 zastąpiono **30/30 w zestawie akceptacyjnym**. Ten zestaw był oglądany podczas rozbudowy i nie jest już niezależnym sprawdzianem. Dodatkowy zestaw 24 sformułowań zamrożono przed implementacją: pierwszy wynik **23/24**, bez błędnej odpowiedzi; jeden brak odczytu dotyczył odmiany „nierównych boków”. Po uzupełnieniu słownika jest **24/24**, co należy traktować jako wynik po naprawie. Wszystkie **12 kontroli brakujących lub sprzecznych danych** nadal zatrzymuje odpowiedź.

Pełny zestaw regresji po zmianach: **1040 testów przeszło**. W działającym formularzu sprawdzono przeciwne kwantyfikatory, widoczne przykłady kątów i współrzędnych, błędne dane, ekran mobilny i brak błędów JavaScript. Do testów negatywnych użyto osobnego banku, bez lekcji użytkownika.

## Co zostało wdrożone

Pytanie jest odczytywane jako klasa figur, warunki, własność, kwantyfikator i zakres negacji. „Każdy romb ma równe przekątne” i „Istnieje romb z równymi przekątnymi” otrzymują różne odpowiedzi: odpowiednio **nie** i **tak**. „Nie może” oznacza brak dopuszczalnego przykładu; „każdy nie jest” sprawdza zanegowaną własność dla każdej figury, bez odwracania zakresu negacji.

Dla trójkątów model stosuje dodatnie kąty o sumie 180°, zależność równości boków i przeciwległych kątów oraz klasy: równoboczny, równoramienny, różnoboczny, prostokątny, ostrokątny i rozwartokątny. Dokładna eliminacja liniowych nierówności na ułamkach rozstrzyga istnienie modelu i odtwarza jego kąty. Obsługiwane są m.in. największy kąt, liczba kątów prostych/rozwartych, dane dwóch lub trzech kątów oraz nierówność trójkąta dla trzech długości w tej samej obsługiwanej jednostce.

Dla czworokątów prawdziwe twierdzenia ogólne wynikają z jawnych definicji i własności klas. Przeciwprzykłady oraz potwierdzenia istnienia są sprawdzane na dokładnych współrzędnych. Skończona lista przykładów **nie służy do dowodzenia twierdzeń ogólnych**. Gdy brakuje twierdzenia i sprawdzonego przykładu, czytnik nie zgaduje.

Formularz pokazuje odczyt „dla każdej” / „istnieje” oraz konkretne kąty lub wierzchołki przykładu, gdy występuje. Dodano cztery przyciski przykładów. Wybrane instrukcje arkuszowe i listy odpowiedzi są rozbijane na pytania z zachowaniem wszystkich opcji. Nieznana opcja oznacza wynik częściowy; nie jest usuwana.

To **rozbudowa kontrolowanego czytnika i jawnego modelu matematycznego**, nie nowy trening oryginalnego rdzenia neuronowego. Oryginalne modele są zachowane.

## Ponowne sprawdzenie ZPE

| Stan w tym samym zestawie 204 wpisów | Poprzednio | Teraz |
|---|---:|---:|
| Kompletne poprawne odpowiedzi | 15 | **41** |
| Wykonania częściowe | 4 | **5** |
| Bez rozwiązania | 185 | **158** |

26 nowych kompletnych odpowiedzi sprawdzono merytorycznie według sumy kątów, zależności boków i kątów, symetrii, definicji klas oraz własności przekątnych. Wcześniejsze 15 poprawnych odpowiedzi również sprawdzono ponownie. Dodatkowy wynik częściowy dotyczy listy własności wielokątów, w której część zdań nadal nie jest rozpoznana.

Zestaw obejmuje 129 numerowanych ćwiczeń, warianty źródłowe i wyodrębnione zdania. **41/204 nie oznacza wyniku dla 204 niezależnych zadań.** Konstrukcje, brakujące ilustracje, złożone tabele, ortocentrum, liczne inne własności i dowolny język pozostają poza tym wdrożeniem.

## Przykłady

| Pytanie | Odpowiedź |
|---|---|
| Czy każdy romb ma równe przekątne? | Nie; sprawdzony romb o nierównych przekątnych |
| Czy istnieje romb z równymi przekątnymi? | Tak; kwadrat |
| Czy trójkąt równoramienny może być rozwartokątny? | Tak; dodatnie kąty o sumie 180°, dwa równe i jeden rozwarty |
| Czy trójkąt może mieć dwa kąty proste? | Nie; trzeci musiałby być niedodatni |
| Czy istnieje trójkąt, w którym największy kąt ma 50°? | Nie; suma nie przekroczyłaby 150° |

[Wcześniejsza diagnoza](DIAGNOZA_ZPE_2026-10-17.md) · [Historia projektu](HISTORIA_PROJEKTU.md)
