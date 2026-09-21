# RDP-004: Galeria i obrazy realizacji

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-003, RDP-005, RDP-006, RDP-007  
**Zakres:** organizacja, optymalizacja i prezentacja zdjęć realizacji

## 1. Organizacja plików

Każda realizacja jest przechowywana jako jeden samowystarczalny katalog przypisany do jej slugu. W tym samym katalogu znajdują się plik Markdown realizacji oraz wszystkie jej obrazy. Przykładowa organizacja:

```text
src/content/portfolio/
└── [slug-realizacji]/
    ├── index.md
    ├── hero.jpg
    ├── widok-ogolny.jpg
    └── detal-kwiatow.jpg
```

Folder realizacji zawiera:

- plik Markdown z metadanymi oraz opisem,
- zdjęcie hero / reprezentacyjne,
- zdjęcia do galerii,
- opcjonalne zdjęcia wykorzystywane w treści Markdown.

Ten sam plik obrazu może występować w galerii i być osadzony w opisie Markdown. Nie tworzy się jego kopii dla każdego zastosowania.

W katalogu `/public/` nie przechowuje się ani nie wykorzystuje zdjęć realizacji. Zdjęcia realizacji nie mogą też być linkowane z zewnętrznych serwisów. Wszystkie obrazy są lokalnymi plikami importowanymi z katalogu danej realizacji, aby Astro mógł je przetworzyć przy budowaniu strony.

Nazwy plików muszą być jednoznaczne i czytelne, małymi literami, z wyrazami oddzielonymi myślnikami. Opis alternatywny każdego zdjęcia jest przechowywany w danych realizacji lub bezpośrednio obok deklaracji obrazu; nie może wynikać wyłącznie z nazwy pliku.

## 2. Optymalizacja obrazów

- Obrazy źródłowe są przetwarzane automatycznie podczas budowania strony przez mechanizm obrazów Astro.
- Publicznie serwowane obrazy mają format AVIF. Dopuszczalny jest format zapasowy, gdy przeglądarka nie obsługuje AVIF.
- Dla każdego miejsca użycia powstają warianty rozmiarów dopasowane do rzeczywistej szerokości: karta, hero, treść i galeria.
- Kod strony korzysta z responsywnych źródeł obrazów, aby przeglądarka pobierała możliwie najmniejszy właściwy plik.
- Należy ustalać wymiary lub proporcje obrazu przed jego załadowaniem, aby zapobiegać przesunięciom układu.
- Obraz hero oraz zdjęcia widoczne w pierwszym widoku mają priorytet ładowania adekwatny do ich znaczenia. Pozostałe zdjęcia, w tym dalsze elementy galerii, ładują się leniwie.

## 3. Galeria jako komponent wielokrotnego użytku

Galeria jest niezależnym komponentem, który można wykorzystać na stronie szczegółowej realizacji oraz w innych miejscach witryny, np. na stronie głównej, w ofercie lub w artykule blogowym. Komponent przyjmuje lokalną listę obrazów z ich tekstami alternatywnymi oraz opcjonalny tytuł sekcji; nie jest na stałe związany z Portfolio.

Na stronie szczegółowej realizacji galeria jest ostatnią częścią merytoryczną, przed wezwaniem do kontaktu. Lista zdjęć galerii jest generowana z plików zapisanych w katalogu tej realizacji. Zdjęcie hero może, ale nie musi, należeć do tej listy.

- Zdjęcia są przedstawione w responsywnej siatce.
- Na telefonie układ pozostaje czytelny i wygodny do dotknięcia; na większych ekranach liczba kolumn może wzrosnąć.
- Miniatury zachowują spójne proporcje lub świadomie dobrany układ typu masonry; wybór zostanie podjęty w etapie projektu wizualnego. Niezależnie od wariantu galeria nie może powodować skoków układu.
- Kliknięcie lub dotknięcie zdjęcia otwiera lightbox z większą wersją obrazu.

## 4. Lightbox

Lightbox umożliwia oglądanie zdjęć jednej realizacji w powiększeniu oraz przechodzenie do poprzedniego i następnego zdjęcia.

- Otwiera się po wybraniu miniatury i pokazuje aktualne zdjęcie.
- Zawiera przycisk zamknięcia oraz kontrolki poprzednie / następne, gdy galeria ma więcej niż jedno zdjęcie.
- Na telefonie obsługuje wygodne sterowanie dotykiem; nie wymaga gestu przesunięcia do podstawowego działania.
- Na klawiaturze: `Escape` zamyka lightbox, a widoczne kontrolki można obsłużyć klawiszem Tab i Enter/Spacja.
- Po zamknięciu fokus wraca do miniatury, z której otwarto lightbox.
- Lightbox ma czytelną nazwę zdjęcia lub jego opis alternatywny dla technologii asystujących.
- Nie pobiera dużych wersji wszystkich obrazów przed otwarciem galerii.

## 5. Kryteria akceptacji

1. Każda realizacja ma własny katalog zawierający jej Markdown i wszystkie lokalne zdjęcia.
2. Budowanie strony tworzy zoptymalizowane warianty AVIF obrazów bez ręcznej konwersji każdego pliku.
3. Karty, hero, treść i galeria używają obrazów o adekwatnych rozmiarach.
4. Galeria jest responsywna, a każde zdjęcie można otworzyć w lightboxie.
5. Lightbox jest użyteczny myszą, dotykiem i klawiaturą.
6. Zdjęcia realizacji nie są ładowane z `/public/` ani z internetu.
7. Ten sam komponent galerii można użyć poza Portfolio, przekazując mu inną lokalną listę obrazów.
