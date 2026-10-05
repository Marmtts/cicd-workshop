# Baseline — pomiar stanu wyjściowego

Plik uzupełniasz w ZADANIU 01. Czasy odczytujesz w zakładce **Actions**. Wystarczy dokładność
do sekundy.

## Czasy kroków — przebieg na `main`

| Krok | Czas |
|---|---|
| Set up job | 0s |
| Checkout | 1s |
| Set up Node | 1s |
| Install dependencies | 6s |
| Install Playwright browsers | 17s |
| Unit tests | 1s |
| API tests | 20s |
| UI tests | 2m 27s |
| Upload Playwright report | 1s |
| Post Set up Node | 1s |
| Post Checkout | 0s |
| Complete job | 0s |
| **Cały przebieg** | 3m 15s  |

## Czas do pierwszego czerwonego sygnału

| Branch | Czas samego testu | Od startu przebiegu do informacji o błędzie |
|---|---|---|
| `demo/failing-unit` | | |
| `demo/failing-search` | — | |

Co na `demo/failing-unit` stało się z testami API i UI:

## `demo/failing-lint` i `demo/failing-security`

| Branch | Wynik przebiegu | Dlaczego tak |
|---|---|---|
| `demo/failing-lint` | | |
| `demo/failing-security` | | |

## Pięć problemów obecnego pipeline’u

1.
2.
3.
4.
5.

## Pomiary z kolejnych zadań

Tu dopisujesz pomiary i odpowiedzi z kolejnych zadań, pod nagłówkiem z numerem zadania.

## Zadanie 03

Czasy runów:

| Krok | Run 1 | Run 2 |
|---|---|---|
|  Install dependencies | 4s | 4s |
|  Install Playwright browsers, | 8s | 0s |
|  całkowity czas przebiegu | 3m 21s | 3m 11s |

## Zadanie 04

- czy lint, testy jednostkowe i build zależą od siebie, czy mogą wystartować równolegle?  - Mogą
- czy testy API i UI powinny wystartować, jeśli aplikacja się nie buduje? - Nie
- czy warto uruchamiać drogie testy API i UI, jeśli lint albo testy jednostkowe już wykryły problem? - Nie
- na co testy API i UI czekają, bo muszą, a na co tylko dlatego, że tak zdecydowaliśmy? - Czekają na build, quality, unit

- czas całego przebiegu — 2m 59s
- sumę czasów wszystkich jobów — 3m 47s

## Zadanie 05

| Krok | Zadanie 04 | Zadanie 05 |
|---|---|---|
|  Ile razy budowana jest aplikacja | 3 | 1 |
|  Czas joba UI tests | 2m 48s | 2m 40s |
|  Suma czasów wszystkich jobów | 3m 11s | 3m 2s |

## Zadanie 06

- Czas joba security - 12s
- Całkowity czas przebiegu - 3m 14s
- Po 9s znaleziono error

- czy według Ciebie job Security powinien blokować scalenie pull requesta, czy tylko ostrzegać, oraz dlaczego:
- - Powinien blokować scalenie Pull Requesta z powodu wpływu na bezpieczeństwo aplikacji

## Zadanie 07


| Krok | Zadanie 06 | Zadanie 07 |
|---|---|---|
| Czas UI tests na pull requeście | 2m 49s | 24s |
| Czas UI tests na main | 2m 49s | 2m 27s |
|  Całkowity czas przebiegu pull requesta| 3m 11s | 3m 2s |
| Liczba testów UI na pull requeście | 123 | 5 |

## Zadanie 08

Testy UI nie importują kodu aplikacji, tylko otwierają ją w przeglądarce, więc --only-changed zmiany w kodzie nie widzi. 

- Zmiana tylko w README.md - 28s
- Zmiana w src/web/	- 55s
- Pull request bez selektywności (wynik z ZADANIA 07)	3m 46s

