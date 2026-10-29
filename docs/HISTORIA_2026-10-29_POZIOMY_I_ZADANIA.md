# 29 października 2026 — poziomy geometrii i bank zadań

- Powiązanie dodatkowych pól z poziomem i figurą; podstawowy, licealny i akademicki.
- 13 rodzin dodatkowych zależności licealnych oraz całki dla 16 modeli figur i brył. Model beczki zakłada paraboliczny profil promienia; całki brył dotyczą objętości, nie dowolnej powierzchni parametrycznej.
- Dokładne obliczenia SymPy, jawne jednostki, walidacja dodatnich wymiarów, nierówności trójkąta, kątów i ograniczeń rombu/beczki.
- Wdrożenie do wspólnego modułu integrated_math używanego przez walidator oraz do lokalnej kopii jego narzędzi. Nie zmieniano wag TSI.
- Formularz nauczyciela: wzór z istniejącego zadania, kopiowanie bez identyfikatora i rewizji oryginału, przejście do działu i konkretnego zadania. Uwierzytelnianie pozostaje wymagane.
- Testy: pięć grup testów solvera, każda dostępna para model–figura, przykłady z oczekiwanymi wynikami, błędne dane, jednostki i język. Sprawdzono rzeczywiste odpowiedzi API i UI: trójkąt 3–4–5 → 90°; walec r=3, h=5 → 45π cm³.
- Formularz nauczyciela sprawdzany na oddzielnej bazie testowej; zapis kopii nie zawiera id/revision oryginału. Produkcyjne zadania nie były modyfikowane w testach.
- Kopie poprzednich plików zachowano w backups/teacher-levels-20261029. Nowe funkcje nie zostały spakowane do opublikowanego demo.
