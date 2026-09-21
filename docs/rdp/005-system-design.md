# RDP-005: System Design

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-003, RDP-004, RDP-006  
**Zakres:** wspólne zasady wizualne, tokeny projektu, komponenty i dostępność interfejsu

## 1. Charakter wizualny

Interfejs Projekt Papier jest lekki, artystyczny i uporządkowany. Priorytetem są fotografie realizacji oraz czytelna treść, a nie dekoracyjność interfejsu. Wszystkie strony i komponenty używają tego samego systemu kolorów, typografii, odstępów oraz stanów interaktywnych.

## 2. Tokeny kolorów i motywy

- Obecnym motywem domyślnym jest motyw inspirowany aktualną stroną: fuksja jako główny akcent, zieleń jako akcent pomocniczy, biel oraz bardzo jasny beż jako powierzchnie tła.
- Kolory nie są wpisywane bezpośrednio w klasach poszczególnych komponentów. Komponenty używają wyłącznie nazw semantycznych, np. `brand`, `accent`, `surface`, `surface-muted`, `foreground`, `muted` i `border`.
- Semantyczne nazwy są mapowane do kolorów Tailwind lub własnych wartości motywu w jednym centralnym miejscu konfiguracji systemu designu.
- Zmiana motywu w przyszłości polega na podmianie wartości tokenów w tym jednym miejscu — na inne kolory Tailwind albo własne wartości — bez zmiany klas w kartach, menu, przyciskach, galerii czy stopce.
- W pierwszym motywie token `brand` odpowiada za fuksję, `accent` za zieleń, `surface` za biel, a `surface-muted` za bardzo jasny beż.
- Kontrast tekstu, linków, przycisków i stanu focus musi pozostać zgodny z wymaganiami dostępności po każdej zmianie motywu. Kolor nigdy nie jest jedynym nośnikiem informacji.

## 3. Typografia i elementy wspólne

- Typografia jest spójna na stronie listy, w szczegółach realizacji, galerii, nagłówku i stopce.
- Nagłówki tworzą wyraźną hierarchię, a tekst opisowy pozostaje łatwy do czytania.
- Dokładne rodziny fontów i ich skala są definiowane jako tokeny systemu designu. Ich ładowanie nie może blokować pierwszego widoku strony.
- Wspólne elementy (karta, tag, przycisk, link, paginacja, galeria, nagłówek i stopka) mają jednolite odstępy, promienie, typografię i stany hover, focus oraz aktywny.

## 4. Zasady implementacji stylów

- Strony są budowane w Astro z Tailwind CSS.
- Do stylowania należy w pierwszej kolejności używać standardowych klas narzędziowych Tailwind.
- Własne klasy CSS są dopuszczalne wyłącznie dla globalnych tokenów projektu lub reguł, których nie można rozsądnie wyrazić klasami Tailwind, np. części lightboxa.
- Reguły maksymalnej szerokości treści, odstępów i breakpointów opisuje RDP-006.
- Interaktywne elementy mają widoczny stan focus, hover i aktywny. Stan focus działa również podczas obsługi klawiaturą.

## 5. Dostępność

- Struktura HTML jest semantyczna: `header`, `nav`, `main`, `article`, sekcje z nagłówkami, lista kart oraz `footer` tam, gdzie odpowiadają znaczeniu treści.
- Kolejność fokusu odpowiada kolejności wizualnej i logicznej.
- Wszystkie obrazy mają odpowiednie teksty alternatywne; obraz czysto dekoracyjny może mieć pusty tekst alternatywny.
- Tekst, przyciski, menu i kontrolki galerii są czytelne oraz wygodne do użycia dotykiem i klawiaturą.

## 6. Kryteria akceptacji

1. Wszystkie strony używają spójnego systemu kolorów, typografii i stanów interaktywnych.
2. Komponenty nie zawierają na stałe wartości konkretnych kolorów marki.
3. Zmiana wartości tokenów umożliwia utworzenie nowego motywu bez edytowania komponentów.
4. Fuksja jest głównym akcentem obecnego motywu, zieleń pomocniczym, a tła są białe lub bardzo jasnobeżowe.
5. Każdy motyw zachowuje kontrast i widoczne stany focus.
