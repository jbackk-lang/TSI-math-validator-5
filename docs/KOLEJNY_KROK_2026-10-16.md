# Jeden przebieg i kolejne kierunki TSI

Stan: 16 października 2026.

## Działający wspólny przebieg

W zwykłych zadaniach tekstowych nowa matryca stanowi kolejną metodę po dotychczasowym czytniku. Nie zastępuje poprawnie działających wzorców geometrii, równań i optymalizacji. Dla obsługiwanych opisów buduje wiersze zależności, wskazuje niewiadome, przyjmuje ich wartości w tym samym formularzu i liczy dokładny wynik.

Przykłady: `pomnóż sumę 3 i 4 przez 2`, `dzielimy bok naprzeciw kąta przez bok przy kącie`, `licznik to bok przyległy do kąta. Mianownik to przeciwprostokątna.`

Nowe nazwy boków i konstrukcja dzielenia mają jawne definicje symboliczne. Pełny odczyt kontrolowany przygotowuje sześć kanonicznych klas roli i rodzaju boku. Istniejąca wytrenowana sieć potwierdza klasy; odpowiedź jest przyjmowana tylko przy zgodności i pewności co najmniej 0,9. Nie przeprowadzono nowego treningu ani wymiany głównego modelu. Poprawa zakresu pochodzi z połączenia sieci, nauczonych jawnie znaczeń i kontroli wszystkich fragmentów wejścia.

## Potwierdzone poprawki

Strona `/lekcje` udostępnia lokalny bank przykładów. Nieudane odczyty z formularza trafiają do kolejki bez etykiety prawidłowej odpowiedzi. Użytkownik może podać wzór, wyjaśnienie i potwierdzić interpretację. Narzędzie sprawdza składnię i dziedzinę wzoru; nie udaje, że rachunek dowodzi znaczenia opisu.

Potwierdzony przykład otrzymuje stały przydział: lekcja albo odłożony sprawdzian. Identyczne treści po ujednoliceniu wielkości liter i odstępów nie tworzą duplikatów ani nie mogą trafić do obu zbiorów. Sprzeczne potwierdzone interpretacje są odrzucane do rozstrzygnięcia. Równoważne parafrazy wymagają dodatkowego audytu — sam klucz treści nie zapewnia pełnego rozdzielenia znaczeniowego.

Oba zbiory można pobrać jako JSON. Zapisy i eksport nie uruchamiają treningu, nie zmieniają wag ani nie wprowadzają poprawek automatycznie do bieżących odpowiedzi.

## Następne zastosowania

Pierwszy kierunek to szersza matematyka opisowa przy zachowaniu jawnych ról, jednostek, dziedziny i sprawdzania wyniku. Kolejne rodziny wymagają własnych definicji, przykładów i odłożonych testów.

Drugi kierunek to dokumenty i MUZ: pochodzenie każdej odczytanej kwoty, zależności między danymi i rozdzielenie faktów od kategorii proponowanych regułami. Dane użytkownika pozostają lokalnie. Kontrola rachunków nie potwierdza kompletności ani prawdziwości dokumentu.

Trzeci kierunek to uczenie na potwierdzonych poprawkach. Obecnie działa gromadzenie i rozdzielanie przykładów. Właściwy trening kolejnych wag wymaga osobnego protokołu, kontroli regresji i niezależnego sprawdzianu przed wdrożeniem.
