# Pochodzenie nowego komponentu

Wariant łączy numerycznie oceny trzech wyuczonych elementów: dotychczasowego menedżera TSI, jego wcześniejszej wersji uczonej z powtórkami oraz odczytu wektorów polskiego enkodera. Podczas przewidywania nie korzysta z listy oczekiwanych odpowiedzi ani reguł przypisujących konkretne zdania do klas.

Wcześniejsze uczenie języka dostarcza **HerBERT base cased**, autorstwa Mroczkowskiego, Rybaka, Wróblewskiej i Gawlika (Allegro / IPI PAN), na licencji **CC BY 4.0**. [Oryginalny model i karta](https://huggingface.co/allegro/herbert-base-cased), [licencja](https://creativecommons.org/licenses/by/4.0/). Użyta rewizja: `50e33e0567be0c0b313832314c586e3df0dc2297`.

Modyfikacje: lokalna konwersja wag enkodera do safetensors bez zmiany jego parametrów, wyuczony osobno odczyt celu oraz numeryczna kombinacja z ocenami modeli TSI. Wariant ten ma zamrożony enkoder HerBERT. Próba dostrajania jego górnych warstw jest odrębnym doświadczeniem. Wiedza językowa HerBERT-a nie jest wynikiem samouczenia TSI od zera. Obliczenia odbywają się lokalnie.

Zakres: pięć celów polecenia po polsku; wyrażenie matematyczne i zakres wykresu są podawane osobno. Dane testowe są syntetyczne. Wynik nie stanowi dowodu uniwersalnego rozumienia języka ani skuteczności dla rzeczywistej populacji użytkowników. Oryginalnego rdzenia wektorowego TSI nie zastąpiono.

Współczynniki wybrano na wcześniej ujawnionych danych roboczych, wymagając zachowania poprawnych odpowiedzi. Oddzielny finał 80 poleceń jest oceniany dopiero dla wybranego wariantu; jego wynik nie służy do zmiany współczynników tej próby.

Ten wariant dodatkowo dostraja dwie górne warstwy HerBERT-a, pooler i głowicę klasyfikacji. Dolne10 warstw i embeddingi są zamrożone. Wyuczony dodatek modyfikuje oceny zamrożonego wcześniejszego menedżera. Jest porównywany także ze wszystkimi poprawnymi odpowiedziami pośredniego wdrożonego zespołu modeli.
