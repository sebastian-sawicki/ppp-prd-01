# RDP-003: Portfolio — szczegół realizacji

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-004, RDP-005  
**Zakres:** podstrony pojedynczych realizacji pod adresem `/portfolio/[slug]/`

## 1. Cel

Każda podstrona realizacji opowiada pełną historię projektu: czym był, dla kogo powstał, jaki miał charakter i jak wyglądał. Strona ma budować zaufanie oraz kierować zainteresowaną osobę do kontaktu.

## 2. Wymagany układ treści

1. Wspólny nagłówek z aktywną pozycją Portfolio.
2. Sekcja hero zawierająca tytuł realizacji oraz to samo zdjęcie reprezentacyjne, które występuje na jej karcie listy.
3. Tagi kategorii realizacji.
4. Informacja „Dla kogo” — klient, marka, instytucja albo rodzaj odbiorcy projektu.
5. Długi, wartościowy opis realizacji.
6. Galeria zdjęć realizacji zgodna z RDP-004.
7. Wezwanie do działania prowadzące do `/kontakt/`.
8. Wspólna stopka.

Opis realizacji jest tworzony w Markdownie. Musi umożliwiać redakcji użycie nagłówków, akapitów, list, linków, cytatów oraz dodatkowych zdjęć osadzonych w treści. Zdjęcia umieszczone w treści są częścią opowieści i nie zastępują galerii końcowej.

## 3. Dane realizacji

Każda realizacja wymaga co najmniej następujących informacji:

| Pole | Wymaganie |
| --- | --- |
| Tytuł | unikalny i zrozumiały dla odbiorcy |
| Slug | unikalny identyfikator URL |
| Krótki opis | używany na karcie na liście Portfolio |
| Zdjęcie hero | obraz reprezentacyjny używany też na karcie |
| Tekst alternatywny hero | konkretny opis zdjęcia |
| Kategorie | co najmniej jeden tag |
| Dla kogo | klient / marka / instytucja / odbiorca |
| Pełny opis | bogata treść w Markdownie |
| Galeria | co najmniej jedno zdjęcie, jeśli jest dostępne |
| Wyróżniona | wartość określająca kolejność na liście |
| Data | data realizacji lub data publikacji, do celów sortowania i metadanych |

## 4. Zasady treści i SEO

- Tytuł realizacji jest jedynym nagłówkiem H1 strony.
- Nazwy kategorii są prezentowane jako linki lub etykiety, bez udawania przycisków filtrowania, ponieważ filtrowanie nie jest objęte zakresem.
- Informacja „Dla kogo” jest przedstawiona jako zwykła, łatwa do odczytania informacja tekstowa.
- Pełny opis ma wyjaśniać kontekst, zakres prac, efekt i najważniejsze cechy realizacji naturalnym językiem; nie może być wyłącznie zbiorem słów kluczowych.
- Każda realizacja otrzymuje unikalne metadane `title` i `description`, wynikające z jej tytułu i krótkiego opisu.
- Strona zawiera link do kontaktu po galerii; opcjonalnie może zawierać dyskretny link powrotny do `/portfolio/`.

## 5. Responsywność i media

- Zdjęcie hero jest czytelne na telefonie i desktopie, bez ucinania kluczowego motywu obrazu.
- Tekst zachowuje wygodną długość wiersza na szerokich ekranach.
- Obrazy dodawane do treści Markdown oraz do galerii są optymalizowane według RDP-004.
- Galeria i każde powiększone zdjęcie są obsługiwalne klawiaturą i na ekranach dotykowych.

## 6. Kryteria akceptacji

1. Każda strona `/portfolio/[slug]/` zawiera wymagane elementy z sekcji 2 w podanej kolejności funkcjonalnej.
2. Tytuł i zdjęcie hero są zgodne z kartą tej samej realizacji na liście Portfolio.
3. Autor treści może dodać bogaty tekst i obrazy za pomocą Markdowna bez tworzenia osobnej strony.
4. Na stronie widoczne są kategorie i informacja „Dla kogo”.
5. Po treści dostępna jest galeria oraz przejście do strony kontaktowej.

