# TSI: wykonanie planu, kontrola i wznowienie

Stan: 20 października 2026. Wspólny moduł otrzymał wykonawcę `WorkflowRunner` oraz metodę `TSISystem.workflow_reply`. Jest to rozwój oprogramowania; w tym etapie nie zmieniano wag sieci.

## Działa

- Wykonanie jawnego planu do 32 kroków z użyciem zarejestrowanych zdolności TSI.
- Przekazywanie wyniku jednego kroku do następnego; dokładne ułamki i jawne jednostki.
- Sprawdzenie każdego kroku niezależnym kontrolerem wskazanym przez aplikację.
- Trwały zapis postępu, atomowa wymiana pliku oraz blokada równoległego wykonania tego samego zadania.
- Wznowienie w nowej instancji po przerwaniu; ponowne obliczenie kroku bez zatwierdzonego wyniku.
- Wykorzystanie zapisanych wyników, jeśli dane i wersja wykonawcy pozostały takie same. Zmiana danych lub wersji powoduje przeliczenie, a nie bezwarunkowe użycie starego wyniku.
- Przy braku danych lub niepotwierdzonym wyniku: zapis problemu, źródeł, wykonanych kroków i konkretnego pytania. Uzupełnione dane są ponownie sprawdzane przed kontynuacją.

## Wyniki

**37/37 testów** wspólnego modułu i wykonawcy, w tym przerwanie, blokada równoległego wykonania, uszkodzenie zapisu, zmiana wersji, fałszywy wynik oraz wznowienie po korekcie sprzecznych danych.

**12/12 prostych zadań** na rzeczywistych narzędziach: cztery funkcje pierwotne z kontrolą pochodną, cztery projekty budżetu z kontrolą bilansu oraz cztery syntetyczne sygnały z określonymi składnikami. Zapisane wyniki nie były obliczane drugi raz.

**3/3 plany dwukrokowe** z zatrzymaniem i wznowieniem w nowej instancji: odwrotność macierzy i sprawdzenie mnożeniem; projekt budżetu i scenariusz dodatkowego kosztu; analiza dwóch okien sygnału.

Dodatkowo sprawdzono rzeczywiste `TSISystem.workflow_reply`: przerwanie i wznowienie w nowej instancji, użycie wytrenowanej gałęzi oraz zachowanie porównanej odpowiedzi H512. Tryb JSON: **2/2** prób, z wykorzystaniem zapisanego wyniku.

## Co te wyniki oznaczają

Plan i kryteria sprawdzenia podawał test. Wyniki potwierdzają wykonanie i kontynuację jawnie określonej pracy. Nie dowodzą samodzielnego układania dowolnego planu z polecenia tekstowego ani pełnego wykonywania zawodu analityka, zarządcy lub wykładowcy. W analizie sygnałów sprawdzano dane syntetyczne, a w MUZ przygotowanie projektu, bez działań zewnętrznych.

Nie podłączono zewnętrznego AI. Prośba o konsultację jest zapisywana lokalnie. Odpowiedź konsultanta nie staje się automatycznie prawdą ani poleceniem wykonania; aplikacja musi przekazać uzasadnione uzupełnienie danych i ponownie uruchomić sprawdzenie.

Wykonawca obsługuje tylko kroki zadeklarowane jako analiza lub projekt bez skutków zewnętrznych (`read_only`). Nie zapewnia transakcyjnego wznawiania przelewów, wysyłania pism lub innych nieodwracalnych operacji.

## Podłączenie

`core.workflow_runner(state_directory, engine_revision=..., verifiers=...)` tworzy wykonawcę korzystającego z zarejestrowanych narzędzi. Aplikacja musi w wersji wykonawcy uwzględnić użyte modele, narzędzia i własne kontrolery. W danych wejściowych należy przekazywać wersję rzeczywistego źródła, szczególnie gdy jego identyfikator wskazuje na zmieniającą się bazę danych.

`run(task_id, plan, inputs, max_steps=...)` wykonuje lub wznawia zadanie. Odwołanie `{"$input":"pole"}` pobiera wejście; `{"$step":"nazwa.result.wartość"}` pobiera zatwierdzony wynik wcześniejszego kroku. Zmiana planu wymaga nowego identyfikatora zadania.

W rdzeniu ta sama funkcja jest dostępna jako `workflow_reply`. W trybie JSON `python -m tsi_shared` przyjmuje operację `workflow`; stan zapisuje w lokalnym katalogu aplikacji. Domyślnie dostępne są dokładne zależności liniowe oraz kontrola jawnych faktów; narzędzia domenowe i ich kontrolery rejestruje aplikacja gospodarza.

Nie dodano nowej strony dashboardu. Paczki ZIP nie zmieniano. Diagramu architektury nie publikujemy do ukończenia całości.
