# RDP-002: Portfolio — lista realizacji

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-001, RDP-003, RDP-004, RDP-005  
**Zakres:** strona indeksowa Portfolio pod adresem `/portfolio/`

## 1. Cel

Strona Portfolio prezentuje zrealizowane projekty Pracowni Projekt Papier i prowadzi odbiorcę do ich pełnych opisów. Ma być prosta, wizualna, szybka oraz czytelna zarówno na telefonie, jak i na dużym ekranie.

Nie jest wymagane filtrowanie po kategoriach ani ładowanie kolejnych kart bez przejścia na nową stronę. Serwis jest generowany statycznie podczas budowania, a przy większej liczbie realizacji stosowane jest klasyczne stronicowanie.

## 2. Adresy i nawigacja

- Strona listy: `/portfolio/`.
- Kolejne strony listy: `/portfolio/strona/2/`, `/portfolio/strona/3/` itd. Numeracja rozpoczyna się od strony 2; pierwsza strona nie używa numeru w adresie.
- Każda karta prowadzi do pojedynczej realizacji pod adresem `/portfolio/[slug]/`.
- Menu główne wskazuje Portfolio jako aktywną pozycję na stronie listy i na wszystkich jej podstronach.

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

## 6. Responsywność i wydajność

- Projektowanie odbywa się w podejściu mobile first.
- Na małych ekranach karty układają się w jednej kolumnie.
- Wraz z dostępną szerokością siatka przechodzi do dwóch, a na dużych ekranach do trzech kolumn; liczba kolumn nie może pogarszać czytelności zdjęć ani tekstu.
- Zdjęcia kart używają odpowiednio dobranych rozmiarów i nowoczesnych formatów, aby nie pobierać na telefonie obrazów przeznaczonych dla szerokiego ekranu.
- Zdjęcia kart poza pierwszym widokiem mogą ładować się z opóźnieniem. Zdjęcia widoczne po wejściu na stronę nie mogą powodować przesunięć układu podczas ładowania.

## 7. Kryteria akceptacji

1. `/portfolio/` pokazuje kartę dla każdej realizacji przypisanej do bieżącej strony paginacji.
2. Każda karta ma jedno zdjęcie, tytuł, krótki opis i przejście do odpowiedniej strony szczegółowej.
3. Wszystkie realizacje oznaczone jako wyróżnione pojawiają się przed niewyróżnionymi.
4. Przy większej liczbie realizacji lista używa klasycznej paginacji, a nie filtrowania ani dynamicznego „load more”.
5. Widok jest użyteczny od szerokości telefonu do szerokiego desktopu.
6. Układ nie powoduje zauważalnych przesunięć elementów po załadowaniu zdjęć.

