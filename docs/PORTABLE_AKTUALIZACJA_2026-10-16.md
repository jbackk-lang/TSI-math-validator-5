# Aktualizacja portable — 16 października 2026

Pakiet Windows x64 zawiera pełny kod, modele, odrębny Python i biblioteki. Aktualizacja obejmuje całą stronę geometrii, figury i zależności, obwód i pole z jednostkami, opisy geometryczne, trygonometrię trójkąta prostokątnego, matrycę działań, automatyczny sprawdzany odczyt ról, wspólny formularz zadań, poprawki PL/EN i bank potwierdzonych poprawek.

Na dołączonym Pythonie w trybie izolowanym sprawdzono: zagnieżdżone działania, tangens i cosinus z opisów ról, przeciwprostokątną, odrzucanie dodatkowych warunków, zwykły przebieg zadań, bank potwierdzonych poprawek i zewnętrzną wysokość trójkąta. Dotychczasowy niezakwalifikowany czytnik całych opisów trygonometrycznych pozostaje wyłączony. Zweryfikowano niezmienność 14 chronionych źródeł i modeli.

Uruchomienie po rozpakowaniu całości: START.bat. Zatrzymanie: ZATRZYMAJ.bat. Nie wymaga Pythona zainstalowanego w systemie ani pobierania wag. Dane bieżącej lokalnej aplikacji i prywatne lekcje użytkownika z runtime nie są kopiowane do paczki.

Lokalnie obok ZIP znajduje się plik .sha256. ARCHIVE_VERIFICATION.json w katalogu portable zawiera wynik kontroli CRC, liczbę bajtów i SHA-256 ukończonego archiwum. Kod i ZIP pozostają lokalnie; repozytorium GitHub zawiera tylko dokumentację i zrzuty ekranu. TSI-MUZ jest oddzielnym projektem i nie stanowi części tego ZIP-a.
