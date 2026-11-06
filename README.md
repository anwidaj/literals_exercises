# Literały w C++ — zadania

Pięć [zadań na zajęcia](zadania.md): dwa najprostsze, jedno konkretne i dwa praktyczne. Repozytorium zawiera polecenia i pliki startowe z szablonami do uzupełnienia.

- [Zadanie 1](zadanie1): surowe literały napisowe `R"(...)"`, literały `std::string` (`"..."s`) i literały binarne `0b...`.
- [Zadanie 2](zadanie2): operatory literałów użytkownika przeliczające jednostki pamięci na bajty w `constexpr`.
- [Zadanie 3](zadanie3): typ `Angle` z literałami kątowymi `_deg` i `_rad` oraz przeliczaniem jednostek.
- [Zadanie 4](zadanie4): struktury `Distance` i `Time`, operatory wymiarowe oraz wyliczanie prędkości.
- [Zadanie 5](zadanie5): literał napisowy `operator""_rgb` parsujący kod koloru `#RRGGBB` w czasie kompilacji (`constexpr`).

Wymagany jest kompilator obsługujący **C++17** (lub nowszy) oraz **CMake ≥ 3.16**. Projekty nie wymagają pobierania zewnętrznych bibliotek i działają w pełni offline.

## Budowanie pojedynczego zadania

W katalogu głównym projektu lub w podkatalogu wybranego zadania:

```sh
cmake -S zadanie1 -B zadanie1/build
cmake --build zadanie1/build
```

Uruchomienie programu na Linuxie/macOS:

```sh
./zadanie1/build/program
```

Na Windowsie w PowerShell:

```powershell
.\zadanie1\build\Debug\program.exe
```
