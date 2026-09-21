# RDP-006: Layout, nagłówek i stopka

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-001, RDP-002, RDP-003, RDP-004, RDP-005, RDP-007  
**Zakres:** reguły responsywnego układu, nagłówka i stopki dla całej witryny

## 1. Cel

Ustalić wspólny sposób skalowania układów od telefonu po szeroki desktop oraz zasady stałej nawigacji witryny. Reguły mają chronić czytelność tekstu i jakość zdjęć, a jednocześnie zapobiegać pobieraniu zbyt dużych obrazów na małych ekranach.

Projektowanie rozpoczyna się od telefonu. Klasy responsywne Tailwind są dodawane wyłącznie wtedy, gdy układ wymaga zmiany dla większej szerokości.

## 2. Punkty przełamania

Stosowane są domyślne punkty przełamania Tailwind:

| Prefiks Tailwind | Minimalna szerokość | Zastosowanie |
| --- | ---: | --- |
| bez prefiksu | 0 px | podstawowy widok telefonu |
| `sm:` | 640 px | większe telefony i małe tablety |
| `md:` | 768 px | tablet i początek układu wielokolumnowego |
| `lg:` | 1024 px | laptop i desktop |
| `xl:` | 1280 px | szeroki desktop |
| `2xl:` | 1536 px | bardzo szeroki ekran, tylko gdy wnosi wartość |

Nie tworzy się dodatkowych niestandardowych breakpointów bez konkretnej potrzeby projektowej.

## 3. Szerokości i odstępy

- Główny kontener strony używa pełnej dostępnej szerokości z poziomym paddingiem dla telefonu i narastającym paddingiem na większych ekranach, np. `px-4 sm:px-6 lg:px-8`.
- Zawartość sekcji używa maksymalnej szerokości kontenera, domyślnie `max-w-7xl`, oraz jest wyśrodkowana przez `mx-auto`.
- Długie opisy realizacji mają węższą miarę tekstu, np. `max-w-3xl`, aby nie tworzyć zbyt długich wierszy na desktopie.
- Hero i galeria mogą wykorzystać szerszy kontener niż tekst opisu, lecz pozostają wyrównane do wspólnej osi strony.
- Do odstępów stosuje się skalę Tailwind (`gap-*`, `space-y-*`, `py-*`, `mt-*`) zamiast przypadkowych wartości CSS.

## 4. Nagłówek i menu

Nagłówek jest wspólnym komponentem dostępny na każdej stronie. Zawiera:

- ikonę lub logotyp Pracowni Projekt Papier, będący linkiem do `/`,
- sześć pozycji głównego menu w kolejności z RDP-001: Strona główna, O nas, Oferta, Portfolio, Blog, Kontakt,
- ikonę Instagramu prowadzącą do `https://www.instagram.com/projekt_papier/`,
- ikonę Facebooka prowadzącą do `https://www.facebook.com/profile.php?id=100063452320282/`.

Na desktopie logo, menu oraz ikony społecznościowe tworzą jeden czytelny, poziomy układ. Ikony social media pozostają w górnej części nagłówka, zgodnie z aktualną stroną Projekt Papier.

Na telefonie nagłówek pokazuje logo, ikony Instagramu i Facebooka oraz przycisk menu hamburger. Hamburger ma czytelną etykietę dla technologii asystujących i zmienia stan na otwarty / zamknięty. Po jego otwarciu wyświetla wszystkie sześć pozycji menu w układzie wygodnym do dotyku. Menu może być zamknięte przez ponowne użycie przycisku, klawisz Escape lub wybór pozycji menu.

Aktywna strona menu jest wyraźnie oznaczona w sposób niezależny od samego koloru. Wszystkie ikony i przyciski nagłówka są dostępne z klawiatury i mają opisową nazwę, np. „Instagram Projekt Papier”.

## 5. Stopka

Stopka jest wspólnym komponentem dostępnym na każdej stronie. Powtarza pełne, sześciopozycyjne menu główne oraz te same ikony social media co nagłówek:

- Instagram Projekt Papier: `https://www.instagram.com/projekt_papier/`,
- Facebook Projekt Papier: `https://www.facebook.com/profile.php?id=100063452320282/`.

Linki zewnętrzne są wyraźnie rozpoznawalne, mają opisowe etykiety dostępności i — jeżeli są otwierane w nowej karcie — stosują bezpieczne atrybuty `rel`. Układ stopki na telefonie jest pionowy i czytelny, a na większych ekranach może przechodzić w kilka kolumn.

## 6. Reguły dla komponentów Portfolio

| Element | Telefon | Od `md:` | Od `lg:` |
| --- | --- | --- | --- |
| Siatka kart realizacji | 1 kolumna | 2 kolumny | 3 kolumny |
| Hero realizacji | pełna szerokość kontenera | pełna szerokość kontenera | szeroki kontener, bez nadmiernego rozciągania |
| Tekst opisu | pełna szerokość tekstowego kontenera | ograniczona miara tekstu | `max-w-3xl` lub równoważna |
| Galeria | 1–2 kolumny zależnie od czytelności zdjęć | 2–3 kolumny | 3–4 kolumny |
| Kontrolki lightboxa | duże cele dotykowe | bez zmiany wymagań dostępności | wygodne dla kursora i klawiatury |

Dokładne proporcje obrazów ustala projekt komponentu, ale rezerwuje dla nich miejsce przed pobraniem pliku. Nie należy wymuszać jednego kadru, jeśli prowadziłoby to do utraty kluczowych elementów fotografii.

## 7. Rozmiary i źródła obrazów

- Dla obrazu na karcie, hero, w treści i w galerii Astro tworzy warianty tylko dla szerokości uzasadnionych tymi układami.
- Atrybut `sizes` każdego obrazu odpowiada rzeczywistej liczbie kolumn i maksymalnej szerokości kontenera; dzięki temu urządzenie wybiera odpowiedni wariant źródła.
- Obraz karty nie używa wariantu przeznaczonego dla hero, jeśli nie jest to konieczne dla danego rozmiaru ekranu.
- Obraz hero otrzymuje większe warianty dla szerokich ekranów, ale nie pobiera największego wariantu na telefonie.
- W lightboxie większy obraz jest pobierany dopiero po otwarciu zdjęcia.
- Szczegółowe progi pikselowe wariantów obrazów zostaną wyprowadzone podczas implementacji z docelowych klas kontenera i siatki, aby nie tworzyć nieużywanych plików.

## 8. Kryteria akceptacji

1. Wszystkie komponenty są najpierw użyteczne na ekranie telefonu, bez poziomego przewijania.
2. Układy stosują domyślne breakpointy Tailwind i standardowe klasy narzędziowe.
3. Karty Portfolio przechodzą od jednej do dwóch, a następnie trzech kolumn zgodnie z sekcją 4.
4. Tekst długiego opisu nie rozciąga się bez ograniczeń na dużych ekranach.
5. Obrazy mają responsywne źródła i `sizes` zgodne z rzeczywistym układem.
6. Galeria jako komponent zachowuje czytelność i funkcjonalność na każdym wspieranym rozmiarze ekranu.
7. Nagłówek zawiera logo, sześć pozycji menu oraz ikony Instagrama i Facebooka; na telefonie menu jest dostępne przez hamburger.
8. Stopka powtarza wszystkie pozycje menu oraz oba linki społecznościowe.
