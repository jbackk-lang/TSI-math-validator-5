# Koperta — przykład edytowalny

Dostęp: Geometria → „Przykład · Koperta”. Trzy zestawy danych i edycja a, b, h, d, c; jednostki mm, cm, m; zakładka zamykająca trójkątna lub prostokątna. Siatka przedstawia dwa panele, zamknięcie i trzy zakładki klejowe.

Pole papieru: 2ab + ah/2 + 2bd + ac (trójkąt) lub 2ab + ah + 2bd + ac (prostokąt). Pole jednej strony po złożeniu: ab; powierzchnia obu stron: 2ab. Zakładki zachodzą na panele i nie są ponownie doliczane do powierzchni zewnętrznej.

Dla a=16, b=11, h=4, d=c=1 cm i zamknięcia trójkątnego: pole papieru 422 cm², zamknięcie 32 cm², klejenie 38 cm², jedna strona 176 cm², obie strony 352 cm². Wersja prostokątna przy tych samych wymiarach zużywa 454 cm².

Model edukacyjny pomija grubość papieru i naddatki technologiczne. Wymiary dodatnie, klejenie może wynosić zero. h i c nie przekraczają b; 2d nie przekracza a. Obliczenia wykonuje jawny wzór w interfejsie, nie nowy trening TSI.

## Wybór niewiadomej
Można wyznaczyć a, b, h, d lub c z podanego pola jednej strony, obu stron, zamknięcia, klejenia albo całego papieru. Rozwiązanie jest wyznaczane z zależności liniowej względem jednej wybranej długości, po czym sprawdzane są warunki geometryczne. Jeżeli pole nie zależy od wybranej niewiadomej, panel zgłasza brak możliwości jej wyznaczenia. Sprawdzono: h=4 cm dla P_zakładki=32 cm² i a=16 cm; odrzucenie próby wyznaczenia h z pola jednej strony. Zmiana danych usuwa poprzedni wynik.

## Jeden prostokąt i cztery trójkąty
Drugi przykład ma środkowy prostokąt a × b oraz cztery trójkąty równoramienne. Para górny/dolny: podstawa a, wysokość h1; para lewy/prawy: podstawa b, wysokość h2. Pole papieru ab + a*h1 + b*h2. Rysunki przedstawiają siatkę i skrzydełka złożone do wnętrza prostokąta. Przy 0<h1≤b oraz 0<h2≤a pełne pokrycie tyłu zachodzi dokładnie dla 4*h1*h2≥ab; równość oznacza styk bez nakładania, nierówność ostra — zachodzenie. Sama suma pól skrzydełek nie dowodzi pokrycia. Sprawdzono 49 zestawów przez niezależne próbkowanie przynależności punktów do czterech złożonych trójkątów oraz pięć przypadków obliczeń i walidacji. Przykłady: styk (320 cm²), zachodzenie (346 cm²), szczelina (284 cm²).
