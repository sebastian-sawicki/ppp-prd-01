# RDP-001: Struktura strony i nawigacja

**Status:** propozycja do akceptacji  
**Zakres:** architektura informacji, adresy URL i zasady nawigacji  
**Poza zakresem:** teksty, identyfikacja wizualna, wygląd komponentów, CMS oraz szczegóły techniczne implementacji

## 1. Cel

Zastąpić obecny jednostronicowy landing serwisem wielostronicowym Pracowni Projekt Papier. Nowa strona ma umożliwić odbiorcy szybkie poznanie pracowni, usług i realizacji oraz łatwe przejście do kontaktu.

Strona główna pełni rolę skróconej prezentacji całego serwisu. Pokazuje zajawki najważniejszych obszarów i odsyła do właściwych stron z menu lub ich podstron szczegółowych.

## 2. Główne menu

Główna nawigacja, dostępna na każdej stronie, zawiera dokładnie następujące pozycje:

1. Strona główna
2. O nas
3. Oferta
4. Portfolio
5. Blog
6. Kontakt

Pozycja odpowiadająca bieżącej stronie musi mieć widoczny stan aktywny. Logo w nagłówku prowadzi do strony głównej.

## 3. Mapa serwisu i adresy URL

```text
/
├── /o-nas/
├── /oferta/
│   └── /oferta/[slug]/
├── /portfolio/
│   └── /portfolio/[slug]/
├── /blog/
│   └── /blog/[slug]/
└── /kontakt/
```

| Obszar | Typ strony | Adres |
| --- | --- | --- |
| Strona główna | pojedyncza strona | `/` |
| O nas | pojedyncza strona | `/o-nas/` |
| Oferta | strona indeksowa z kartami | `/oferta/` |
| Szczegół oferty | podstrona usługi | `/oferta/[slug]/` |
| Portfolio | strona indeksowa z kartami | `/portfolio/` |
| Szczegół realizacji | podstrona realizacji | `/portfolio/[slug]/` |
| Blog | strona indeksowa z kartami | `/blog/` |
| Artykuł | podstrona wpisu | `/blog/[slug]/` |
| Kontakt | pojedyncza strona | `/kontakt/` |

`[slug]` jest krótkim, unikalnym identyfikatorem URL tworzonym małymi literami, bez polskich znaków i ze słowami oddzielonymi myślnikami. Przykład: `/oferta/kwiaty-giganty/`.

## 4. Hierarchia stron

### 4.1. Strony pojedyncze

- **O nas** przedstawia pracownię, jej podejście, wartości i sposób pracy. Nie posiada podstron w pierwszej wersji serwisu.
- **Kontakt** zawiera wszystkie kanały kontaktu oraz informacje potrzebne przed rozpoczęciem współpracy. Nie posiada podstron w pierwszej wersji serwisu.

### 4.2. Oferta

`/oferta/` jest katalogiem usług. Każda karta oferty prowadzi do własnej podstrony `/oferta/[slug]/`.

Wstępny zestaw kategorii, wyprowadzony z obecnej strony, obejmuje:

- kwiaty giganty,
- witryny sklepowe,
- dekoracje eventów,
- scenografie,
- instalacje artystyczne,
- obrazy 3D i upominki,
- warsztaty.

Zestaw kategorii może zostać rozszerzony lub zmieniony na etapie osobnego RDP dla oferty, bez zmiany reguł routingu.

### 4.3. Portfolio

`/portfolio/` prezentuje listę realizacji jako karty. Każda karta prowadzi do strony pojedynczej realizacji `/portfolio/[slug]/`.

Każda realizacja może należeć do jednej lub wielu kategorii oferty. Powiązanie to będzie wykorzystane później do filtrowania portfolio i do linków między usługami a realizacjami; nie jest wymagane w pierwszej wersji układu.

### 4.4. Blog

`/blog/` prezentuje listę wpisów jako karty. Każda karta prowadzi do pełnego artykułu `/blog/[slug]/`.

Kategorie, tagi, paginacja i wyszukiwarka bloga nie wchodzą w zakres tego RDP. Należy je określić przed implementacją bloga, jeżeli będą potrzebne.

## 5. Strona główna

Strona główna zawiera skrócone, wybrane sekcje prowadzące do pozostałych obszarów serwisu. Nie zastępuje pełnych podstron.

| Sekcja na stronie głównej | Cel linkowania |
| --- | --- |
| Zajawka „O nas” | `/o-nas/` |
| Wybrane usługi | `/oferta/` lub właściwy szczegół `/oferta/[slug]/` |
| Wybrane realizacje | `/portfolio/` lub właściwy szczegół `/portfolio/[slug]/` |
| Najnowsze / wyróżnione wpisy | `/blog/` lub właściwy artykuł `/blog/[slug]/` |
| Zajawka kontaktu i wezwania do działania | `/kontakt/` |

Na stronie głównej mogą znaleźć się również sekcje wspierające decyzję o kontakcie, np. wyróżniki pracowni, zaufane marki lub opinie. Nie tworzą one osobnych pozycji menu ani samodzielnych adresów URL w tym etapie.

## 6. Wspólne zasady nawigacji

- Nagłówek z głównym menu jest dostępny na wszystkich stronach.
- Stopka zawiera co najmniej skróconą nawigację do sześciu pozycji menu oraz link do strony kontaktowej.
- Użytkownik musi móc przejść z każdej podstrony do strony głównej, oferty, portfolio, bloga i kontaktu bez konieczności używania przycisku „Wstecz”.
- Karty na stronach indeksowych są w całości interaktywne i prowadzą tylko do odpowiadającej im podstrony szczegółowej.
- Na urządzeniach mobilnych menu pozostaje dostępne w formie dostosowanej do małego ekranu.
- Podstrony szczegółowe oferty, portfolio i bloga zawierają link lub wezwanie do działania prowadzące do `/kontakt/`.

## 7. Kryteria akceptacji

1. Serwis ma sześć widocznych pozycji w głównym menu, w kolejności podanej w sekcji 2.
2. Każda pozycja menu prowadzi do unikalnej, działającej trasy z sekcji 3.
3. O nas i Kontakt są pojedynczymi stronami bez listy kart prowadzących do podstron tego samego obszaru.
4. Oferta, Portfolio i Blog mają stronę indeksową z kartami oraz obsługują adresy stron szczegółowych według wzorca `[slug]`.
5. Strona główna zawiera zajawki O nas, Oferty, Portfolio, Bloga i Kontaktu, a każda zajawka zawiera poprawne przejście do właściwego obszaru.
6. Nagłówek i stopka pozwalają dotrzeć do głównych obszarów serwisu z każdej trasy.
7. Bieżąca pozycja menu jest rozróżnialna wizualnie od pozostałych.

## 8. Decyzje do późniejszych RDP

- dokładna zawartość i kolejność sekcji strony głównej,
- pełna lista usług i zakres każdej podstrony oferty,
- model danych oraz filtry portfolio,
- model wpisów, kategorie i paginacja bloga,
- formularz kontaktowy, polityka prywatności i obsługa zgód,
- języki serwisu oraz ewentualne wersje wielojęzyczne.
