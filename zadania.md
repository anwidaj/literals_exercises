# Literały w C++ — zadania

Pięć [zadań na zajęcia](zadania.md): dwa najprostsze, jedno konkretne i dwa praktyczne.

Zadania bazują na materiałach przygotowanych do zajęć (notatki z wykładu o literałach).

---

## 1. Ścieżki i literały wbudowane

**Najprostsze.** W `zadanie1/main.cpp` utwórz surowy literał napisowy `R"(...)"` ze ścieżką do pliku `C:\Gry\MojaGra\save\config.json` oraz wielolinijkowym tekstem z cudzysłowami, bez używania podwójnych ukośników `\\` ani `\"`.

Za pomocą literału `std::string` (`"..."s` z `using namespace std::string_literals;`) połącz dwa napisy  `"Hello"` i `"World"` operatorem `+`.

Zdefiniuj zmienną z literałem binarnym `0b1010'1111` z separatorem cyfr `'` i wypisz jej wartość dziesiętną. Sprawdź:

- ścieżka i wielolinijkowy tekst zachowują ukośniki i cudzysłowy wprost z zapisu;
- czy te dwa napisy tworzą poprawny obiekt `std::string`;
- `0b1010'1111` → `175`.

---

## 2. Jednostki pamięci

**Najprostsze.** W `zadanie2/main.cpp` zdefiniuj w przestrzeni nazw `literals` operatory literałów użytkownika przeliczające jednostki pamięci na liczbę bajtów (`unsigned long long`):

- `_B`, `_KB`, `_MB`, `_GB` dla liczb całkowitych (`unsigned long long`);
- `_KB`, `_MB` dla liczb zmiennoprzecinkowych (`long double`).

Wszystkie operatory oznacz jako `constexpr`.

W `main.cpp` sprawdź w `static_assert`:

- `1_KB` → `1024_B`;
- `1_MB` → `1024_KB`;
- `0.5_KB` → `512_B`;
- `1.5_MB` → `1572864_B`.

Wypisz przykładowe wartości `16_GB` i `64_KB` w bajtach na ekranie.

---

## 3. Przelicznik kątów i kursu

**Konkretne.** W `zadanie3/main.cpp` zdefiniuj strukturę `Angle` z polem `double radians` oraz literały użytkownika w `constexpr`:

- `_deg` (dla `unsigned long long` i `long double`) przeliczające stopnie na radiany: $\text{rad} = \text{deg} \cdot \frac{\pi}{180.0}$;
- `_rad` (dla `unsigned long long` i `long double`) tworzące `Angle` bezpośrednio z radianów.

Przyjmij stałą `constexpr double PI = 3.14159265358979323846;`. Dodaj funkcję `double to_degrees(Angle a)` zwracającą stopnie oraz operator dodawania `Angle + Angle`.

W `main.cpp` sprawdź:

- `180_deg` → wartość w radianach równa `PI` ($\approx 3.14159$);
- `45.5_deg` → `0.79412` rad;
- `90_deg + 45_deg` → kąt odpowiadający `135` stopniom.

---

## 4. Prędkość ze zdefiniowanych jednostek

**Praktyczne.** W `zadanie4/main.cpp` zdefiniuj struktury `Distance` (z polem `double meters`) i `Time` (z polem `double seconds`).

Zaimplementuj literały użytkownika w `constexpr`:

- dla odległości: `_m`, `_km` ($1\text{ km} = 1000\text{ m}$);
- dla czasu: `_s`, `_min` ($60\text{ s}$), `_h` ($3600\text{ s}$).

Zaimplementuj operator dzielenia `Distance / Time` zwracający prędkość w km/h (`double`):
$$\text{predkosc\_kmh} = \frac{\text{dystans w km}}{\text{czas w h}} = \frac{d.meters / 1000.0}{t.seconds / 3600.0}$$

W `main.cpp` sprawdź:

- `150_km / 1.5_h` → `100.0` km/h;
- `30_km / 30_min` → `60.0` km/h.

---

## 5. Literał koloru RGB w czasie kompilacji

**Praktyczne.** W `zadanie5/main.cpp` zdefiniuj strukturę `Color` z polami `int r, g, b` oraz literał napisowy:

```cpp
constexpr Color operator""_rgb(const char* str, std::size_t len);
```

odczytujący pary szesnastkowe dla kanałów R, G, B z napisu formatu `"#RRGGBB"` (obsługuj cyfry `'0'-'9'`, małe `'a'-'f'` i wielkie `'A'-'F'`).

W `main.cpp` sprawdź działanie literału w czasie kompilacji za pomocą `static_assert`:

- `"#FF8000"_rgb` → `r=255, g=128, b=0`;
- `"#00FF00"_rgb` → `r=0, g=255, b=0`;
- `"#000000"_rgb` → `r=0, g=0, b=0`;
- `"#1a2b3c"_rgb` → `r=26, g=43, b=60`.

Wypisz wartości składowych przykładowego koloru na ekranie.
