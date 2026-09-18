# RDP-004: Portfolio — galeria i obrazy

**Status:** propozycja do akceptacji  
**Powiązane dokumenty:** RDP-002, RDP-003, RDP-005  
**Zakres:** organizacja, optymalizacja i prezentacja zdjęć realizacji

## 1. Organizacja plików

Zdjęcia każdej realizacji są przekazywane w osobnym folderze przypisanym do jej slugu. Folder zawiera:

- zdjęcie hero / reprezentacyjne,
- zdjęcia do galerii,
- opcjonalne zdjęcia wykorzystywane w treści Markdown.

Nazwy plików muszą być jednoznaczne i czytelne, małymi literami, z wyrazami oddzielonymi myślnikami. Opis alternatywny każdego zdjęcia jest przechowywany w danych realizacji lub bezpośrednio obok deklaracji obrazu; nie może wynikać wyłącznie z nazwy pliku.

## 2. Optymalizacja obrazów

- Obrazy źródłowe są przetwarzane automatycznie podczas budowania strony.
- Publicznie serwowane obrazy mają format AVIF. Dopuszczalny jest format zapasowy, gdy przeglądarka nie obsługuje AVIF.
- Dla każdego miejsca użycia powstają warianty rozmiarów dopasowane do rzeczywistej szerokości: karta, hero, treść i galeria.
- Kod strony korzysta z responsywnych źródeł obrazów, aby przeglądarka pobierała możliwie najmniejszy właściwy plik.
- Należy ustalać wymiary lub proporcje obrazu przed jego załadowaniem, aby zapobiegać przesunięciom układu.
- Obraz hero oraz zdjęcia widoczne w pierwszym widoku mają priorytet ładowania adekwatny do ich znaczenia. Pozostałe zdjęcia, w tym dalsze elementy galerii, ładują się leniwie.

## 3. Galeria

Galeria jest ostatnią częścią merytoryczną podstrony realizacji, przed wezwaniem do kontaktu.

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

1. Zdjęcia realizacji mogą być dostarczane i utrzymywane w osobnych folderach.
2. Budowanie strony tworzy zoptymalizowane warianty AVIF obrazów bez ręcznej konwersji każdego pliku.
3. Karty, hero, treść i galeria używają obrazów o adekwatnych rozmiarach.
4. Galeria jest responsywna, a każde zdjęcie można otworzyć w lightboxie.
5. Lightbox jest użyteczny myszą, dotykiem i klawiaturą.

