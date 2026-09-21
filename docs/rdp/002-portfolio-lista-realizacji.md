# RDP-002: Portfolio — lista realizacji

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-001, RDP-003, RDP-004, RDP-005, RDP-006, RDP-007  
**Zakres:** strona indeksowa Portfolio pod adresem `/portfolio/`

## 1. Cel

Strona Portfolio prezentuje zrealizowane projekty Pracowni Projekt Papier i prowadzi odbiorcę do ich pełnych opisów. Ma być prosta, wizualna, szybka oraz czytelna zarówno na telefonie, jak i na dużym ekranie.

Serwis jest generowany statycznie podczas budowania. Przy większej liczbie realizacji stosowane jest klasyczne stronicowanie; nie ma ładowania kolejnych kart bez przejścia na nową stronę.

## 2. Adresy i nawigacja

- Strona listy: `/portfolio/`.
- Kolejne strony listy: `/portfolio/strona/2/`, `/portfolio/strona/3/` itd. Numeracja rozpoczyna się od strony 2; pierwsza strona nie używa numeru w adresie.
- Każda karta prowadzi do pojedynczej realizacji pod adresem `/portfolio/[slug]/`.
- Menu główne wskazuje Portfolio jako aktywną pozycję na stronie listy i na wszystkich jej podstronach.

W Astro strona pierwsza oraz strony kolejne są odrębnymi trasami: `/portfolio/` jest generowane przez stronę indeksową, a `/portfolio/strona/[page]/` przez trasę dynamiczną generowaną podczas budowania. Trasa dynamiczna generuje wyłącznie numery od 2 wzwyż, dlatego adres `/portfolio/strona/1/` nie istnieje i nie dubluje strony głównej Portfolio.

## 3. Układ strony

1. Wspólny nagłówek z menu.
2. Krótki nagłówek strony z tytułem `Portfolio` oraz wprowadzeniem.
3. Siatka kart realizacji.
4. Paginacja — wyświetlana wyłącznie, gdy istnieje więcej niż jedna strona wyników.
5. Wspólna stopka.

Strona nie wymaga dodatkowej sekcji „wyróżnione realizacje”. Projekty oznaczone jako wyróżnione są po prostu sortowane przed pozostałymi kartami.

## 4. Karta realizacji

Każda karta zawiera:

- jedno zdjęcie reprezentacyjne,
- tytuł realizacji,
- krótki opis,
- wyraźny link tekstowy lub przycisk prowadzący do pełnej realizacji, np. „Zobacz realizację”.

Cała karta powinna prowadzić do szczegółu realizacji, z zachowaniem prawidłowej dostępności klawiaturowej. Zdjęcie musi mieć opis alternatywny odnoszący się do konkretnej realizacji, a nie ogólny tekst typu „zdjęcie portfolio”.

## 5. Kolejność i stronicowanie

1. Realizacje wyróżnione są wyświetlane jako pierwsze.
2. W obrębie realizacji wyróżnionych i pozostałych domyślną kolejnością jest kolejność ustalona redakcyjnie; w razie jej braku — od najnowszej do najstarszej.
3. Wyróżnienie wpływa tylko na pozycję na liście. Nie wymaga osobnego tła, etykiety ani sekcji.
4. Liczba kart na stronie powinna być stała i ustalona podczas implementacji (rekomendacja: 9 lub 12), z zachowaniem pełnych wierszy na większych ekranach, gdy to możliwe.
5. Paginacja ma linki do poprzedniej i następnej strony, numery stron oraz zrozumiałe etykiety dostępności.
6. Paginacja używa zwykłych linków HTML z atrybutem `href`, dzięki czemu kolejne strony są dostępne bez JavaScriptu dla użytkowników i robotów wyszukiwarek.

## 6. SEO paginacji

- Każda strona paginacji ma własny, samowskazujący adres kanoniczny: `/portfolio/` dla pierwszej strony i właściwy adres `/portfolio/strona/[numer]/` dla każdej strony kolejnej.
- Nie należy ustawiać canonicala strony 2 i kolejnych na `/portfolio/`, ponieważ strony zawierają inne realizacje.
- Paginacja musi umożliwiać przejście sekwencyjne między stronami, a każda strona kolejna powinna zawierać także link powrotny do pierwszej strony Portfolio.
- Nie jest wymagane dodawanie znaczników `rel="next"` i `rel="prev"`; Google ich nie wykorzystuje do obsługi paginacji.
- Strony paginacji są uwzględnione w sitemapie jako samodzielne, kanoniczne adresy.

## 7. Responsywność i wydajność

- Projektowanie odbywa się w podejściu mobile first.
- Na małych ekranach karty układają się w jednej kolumnie.
- Wraz z dostępną szerokością siatka przechodzi do dwóch, a na dużych ekranach do trzech kolumn; liczba kolumn nie może pogarszać czytelności zdjęć ani tekstu.
- Zdjęcia kart używają odpowiednio dobranych rozmiarów i nowoczesnych formatów, aby nie pobierać na telefonie obrazów przeznaczonych dla szerokiego ekranu.
- Zdjęcia kart poza pierwszym widokiem mogą ładować się z opóźnieniem. Zdjęcia widoczne po wejściu na stronę nie mogą powodować przesunięć układu podczas ładowania.

## 8. Kryteria akceptacji

1. `/portfolio/` pokazuje kartę dla każdej realizacji przypisanej do bieżącej strony paginacji.
2. Każda karta ma jedno zdjęcie, tytuł, krótki opis i przejście do odpowiedniej strony szczegółowej.
3. Wszystkie realizacje oznaczone jako wyróżnione pojawiają się przed niewyróżnionymi.
4. Przy większej liczbie realizacji lista używa klasycznej paginacji, bez dynamicznego „load more”.
5. Widok jest użyteczny od szerokości telefonu do szerokiego desktopu.
6. Układ nie powoduje zauważalnych przesunięć elementów po załadowaniu zdjęć.
7. `/portfolio/strona/1/` nie jest generowane, a każda istniejąca strona paginacji ma własny adres kanoniczny i linki HTML do sąsiednich stron.
