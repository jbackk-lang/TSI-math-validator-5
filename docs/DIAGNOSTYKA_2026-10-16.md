# Diagnostyka zapisu i wykresy całek — 16.10.2026

Wprowadzono wspólne sprawdzanie zapisu przed wykonaniem zadania. Diagnostyka zawiera nazwę pola, indeksy początku i końca fragmentu (wewnętrznie od zera), wiersz i kolumnę pokazywane od jednego, opis oraz podpowiedź. Interfejs zaznacza fragment po wykryciu błędu i po wybraniu „Pokaż miejsce błędu”. Nie zmienia sam danych. Edycja usuwa nieaktualne wskazanie. Niepoprawny zapis nie uruchamia obliczenia.

Obsługiwane: brakujące, nadmiarowe i niedopasowane nawiasy, błędy składni/operatorów, puste argumenty funkcji, nieobsługiwane funkcje, brak strony równania; w macierzach błędy JSON, nierówne wiersze, błędne elementy, zerowe mianowniki i niezgodne wymiary. Wskazanie wymiarów dotyczy całej macierzy lub wiersza, nie jednego znaku. Pozostałe błędy matematyczne nadal mogą być zgłaszane ogólnym komunikatem narzędzia. To kontrola obsługiwanego zapisu, nie ogólna ocena sensowności każdego rozumowania.

Dodano wykres całki: f(x) i potwierdzona pierwotna F(x) dla C=0 w trybie nieoznaczonym. W oznaczonym wykres f(x) na przedziale z zaznaczonym obszarem. Uwzględniono kierunek granic w wyniku; rysunek przedstawia przedział w kolejności rosnącej. Punkty nierzeczywiste, nieskończone albo zbyt duże są pomijane. To podgląd próbkowany, nie dowód ani pełna analiza osobliwości. W szczególnych przypadkach biblioteka może nie wyznaczyć pierwotnej lub ciągłości.

Sprawdzenia: **62/62** testy wybranych narzędzi, transportu procesów, diagnostyki oraz wartości i przerw w danych wykresu. Wcześniejszy zestaw etapu akademickiego: 261/261, bez ponownego pełnego uruchamiania w tej aktualizacji. Zestawy częściowo się pokrywają. Dwa przebiegi kontroli przeglądarkowej: wskazanie nawiasu/operatora/pustego argumentu i wiersza macierzy, zachowanie wpisu, brak wywołania obliczenia dla błędu, poprawienie i wykonanie całki oraz macierzy; następnie wykres pierwotnej i funkcji, całka oznaczona z wynikiem 9, widok mobilny i brak błędów JavaScript. 11 chronionych plików oraz aktywny checkpoint bez zmian SHA-256.

Zmiany działają lokalnie. Na GitHub trafiają README, opis etapu i screenshoty, bez kodu, wag i danych treningowych.
