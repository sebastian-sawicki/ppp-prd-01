# RDP-007: SEO i wydajność

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-003, RDP-004, RDP-006  
**Zakres:** widoczność serwisu w wyszukiwarkach i systemach AI oraz szybkość ładowania

## 1. SEO i wyszukiwarki oparte na AI

- Strony są generowane statycznie podczas budowania i udostępniają podstawową treść bez potrzeby wykonania JavaScriptu.
- Każda strona ma unikalny adres kanoniczny, tytuł dokumentu i opis meta.
- Strona listy ma jeden nagłówek H1 `Portfolio`; każda realizacja ma jeden H1 równy jej tytułowi. Kolejne nagłówki tworzą logiczną hierarchię.
- Treść realizacji opisuje projekt konkretnie i naturalnym językiem: rodzaj dekoracji, kontekst, klienta lub odbiorcę (jeżeli można go ujawnić), miejsce oraz rezultat.
- Karty i wpisy używają zwykłych linków HTML z opisowym tekstem. Najważniejsza treść nie może być umieszczona wyłącznie w obrazie, animacji ani interakcji wymagającej JavaScriptu.
- Dane strukturalne dla strony szczegółowej realizacji są dodawane w JSON-LD po potwierdzeniu docelowego typu schema. Odzwierciedlają wyłącznie informacje widoczne na stronie.
- Sitemap obejmuje stronę Portfolio, wszystkie opublikowane realizacje oraz istniejące strony paginacji. Każda z tych stron ma własny, samowskazujący adres kanoniczny.

## 2. Wydajność

- JavaScript jest używany wyłącznie dla niezbędnych interakcji, w tym lightboxa. Lista Portfolio i treść realizacji nie wymagają ciężkiego kodu klienckiego do podstawowego działania.
- Obrazy są przechowywane i przetwarzane zgodnie z RDP-004 oraz używają responsywnych źródeł opisanych w RDP-006.
- Zewnętrzne fonty, skrypty śledzące i osadzenia nie mogą blokować renderowania najważniejszej treści.
- Strona zapewnia szybkie wyświetlenie treści i zdjęcia hero również przy wolniejszym połączeniu mobilnym.
- Należy unikać przesunięć układu po załadowaniu obrazów i fontów.

## 3. Kryteria akceptacji

1. Podstawowa treść Portfolio jest dostępna i zrozumiała bez JavaScriptu.
2. Każda strona ma właściwe metadane, adres kanoniczny i logiczną strukturę nagłówków.
3. Sitemap zawiera wszystkie indeksowalne strony Portfolio.
4. Obrazy, fonty i kod interaktywny nie powodują niepotrzebnego opóźnienia pierwszego widoku.
