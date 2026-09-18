# RDP-005: System stylów, SEO i wydajność dla Portfolio

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-003, RDP-004  
**Zakres:** wspólne zasady wizualne, dostępność, widoczność w wyszukiwarkach i wydajność stron Portfolio

## 1. Charakter wizualny

Portfolio ma kontynuować estetykę obecnej strony Projekt Papier: lekka, artystyczna, uporządkowana i oparta na dużej ilości oddechu. Priorytetem jest fotografia realizacji oraz czytelna treść, nie dekoracyjność interfejsu.

## 2. Kolory i typografia

- Kolorem akcentowym jest fuksja z palety Tailwind. Jest używana oszczędnie: dla głównych linków, przycisków, stanu aktywnego i elementów interaktywnych.
- Zielony jest kolorem pomocniczym, stosowanym w małych akcentach związanych z rękodziełem i ekologicznym charakterem marki.
- Podstawą powierzchni jest biel. Sekcje mogą być delikatnie oddzielane bardzo jasnym odcieniem beżu wpadającego w biel.
- Kolory tekstu muszą zapewniać wystarczający kontrast z tłem. Sama fuksja lub zieleń nie mogą być jedynym sygnałem stanu czy znaczenia.
- Typografia ma być spójna na stronie listy, w szczegółach, galerii i lightboxie. Nagłówki tworzą wyraźną hierarchię, a tekst opisowy jest łatwy do czytania.
- Dokładne rodziny fontów i skale zostaną zdefiniowane w osobnym etapie systemu projektowego; ich ładowanie nie może spowalniać pierwszego widoku.

## 3. Zasady implementacji stylów

- Strony są budowane w Astro z Tailwind CSS.
- Do stylowania należy w pierwszej kolejności używać standardowych klas narzędziowych Tailwind.
- Własne klasy CSS są dopuszczalne wyłącznie dla reguł, których nie można rozsądnie wyrazić klasami Tailwind, np. złożonych części lightboxa lub globalnych tokenów. Nie należy tworzyć zbędnych klas komponentowych dla zwykłych odstępów, kolorów i układów.
- Wspólne elementy Portfolio (karta, nagłówek, tag, przycisk, paginacja, galeria) zachowują te same kolory, odstępy, promienie, stany hover/focus i typografię.
- Interaktywne elementy mają widoczny stan focus, hover i aktywny. Stan focus jest dostępny również przy obsłudze klawiaturą.

## 4. Mobile first i dostępność

- Każdy układ rozpoczyna się od wariantu mobilnego i rozszerza dla większych szerokości.
- Tekst, przyciski i kontrolki galerii pozostają czytelne oraz łatwe do użycia dotykiem.
- Struktura HTML jest semantyczna: `header`, `nav`, `main`, `article`, sekcje z nagłówkami, lista kart oraz `footer` tam, gdzie odpowiadają znaczeniu treści.
- Kolejność fokusu odpowiada kolejności wizualnej i logicznej.
- Wszystkie obrazy mają odpowiednie teksty alternatywne; obraz czysto dekoracyjny może mieć pusty tekst alternatywny.

## 5. SEO i wyszukiwarki oparte na AI

- Strony są generowane statycznie podczas budowania, dostępne bez konieczności wykonania JavaScriptu do odczytania podstawowej treści.
- Każda strona ma unikalny adres kanoniczny, tytuł dokumentu i opis meta.
- Strona listy ma jeden nagłówek H1 `Portfolio`; każda realizacja ma jeden H1 równy jej tytułowi. Kolejne nagłówki tworzą logiczną, niewybraną wyłącznie dla wyglądu hierarchię.
- Treść realizacji opisuje projekt konkretnie i wprost: rodzaj dekoracji, kontekst, klienta lub odbiorcę (jeżeli można go ujawnić), miejsce oraz rezultat. Ułatwia to zrozumienie treści przez wyszukiwarki i systemy AI.
- Karty i wpisy używają zwykłych linków HTML z opisowym tekstem. Najważniejsza treść nie jest umieszczana wyłącznie w obrazie, animacji lub interakcji wymagającej JavaScriptu.
- Dane strukturalne dla strony szczegółowej realizacji są dodawane w formacie JSON-LD po potwierdzeniu docelowego typu schematu. Muszą odzwierciedlać faktycznie widoczne informacje, bez sztucznego wzbogacania.
- Należy wygenerować sitemapę obejmującą stronę Portfolio oraz wszystkie opublikowane realizacje. Strony paginacji nie powinny rywalizować z główną stroną Portfolio o ten sam cel wyszukiwania.

## 6. Wydajność

- JavaScript jest używany tylko dla niezbędnych interakcji, w tym lightboxa; strona listy i treść realizacji nie wymagają ciężkiego kodu klienckiego do podstawowego działania.
- Obrazy są obsługiwane zgodnie z RDP-004.
- Zewnętrzne fonty, skrypty śledzące i osadzenia nie mogą blokować renderowania najważniejszej treści.
- Strona powinna zapewnić szybkie wyświetlenie treści i zdjęcia hero również przy wolniejszym połączeniu mobilnym.

## 7. Kryteria akceptacji

1. Wszystkie strony Portfolio używają spójnego systemu kolorów, typografii i stanów interaktywnych.
2. Fuksja pełni rolę dominującego akcentu, zieleń pomocniczego, a tła są białe lub bardzo jasnobeżowe.
3. Widok mobilny jest punktem wyjścia dla każdego komponentu.
4. Podstawowe treści są dostępne i zrozumiałe bez JavaScriptu.
5. Każda strona ma unikalne metadane i logiczną strukturę nagłówków.
6. Obrazy, fonty i kod interaktywny nie powodują niepotrzebnego opóźnienia załadowania strony.

