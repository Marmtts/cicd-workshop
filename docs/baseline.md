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


## Zadanie 09

| Krok | workers | shardowanie |
|---|---|---|
| Co skaluje|procesy na jednej maszynie | liczbę maszyn|
| Mechanizm	| workers w playwright.config.ts	| strategy.matrix + --shard|
|  Twardy limit| rdzenie runnera |	20 jobów naraz (konto Free)|
| Koszt w minutach | ? | ? |

- - Przed:
- czas joba UI tests - 2m 46s
- łączny czas wszystkich jobów ze strony Usage - 4m 20s
- - Po workers:
- czas joba UI tests - 58s
- łączny czas wszystkich jobów ze strony Usage - 2m 16s	
- - Po Shardowaniu:
- czas joba UI tests - 42s
- łączny czas wszystkich jobów ze strony Usage -  3m 42s
- - 8 shards:
- czas joba UI tests - 38s
- łączny czas wszystkich jobów ze strony Usage - 5m 17s

Gdy jeden z shardów failuje, reszta kontynuuje i kończy testy.

## Zadanie 10


| Co |PR (2 shardy)	|main (8 shardów)|	main (4 shardy, z ZADANIA 09)|
|---|---|---|---|
|Czas najdłuższego sharda |24s|33s|42s|
| Łączny czas jobów (Usage)|1m 53s	|5m 6s	|3m 42s|
|Suma testów ze shardów |5|123|123|
| Jobów jednocześnie w szczycie||||


## Zadanie 11


|Co|	Przed|	Po|
|---|---|---|
| Liczba raportów, które trzeba otworzyć, żeby zobaczyć pełny wynik	|8 (albo 4)|	1|
| Czy raport powstaje przy błędzie| Nie|	Tak|
|  Czas joba UI report	|—	|21s|

## Zadanie 12

|Co	|ZADANIE 01	|Po ZADANIU 12|
|---|---|---|
|Czy trzeba coś pobierać	|tak	|nie|
|Czas joba Test report|	—	|7s|

## Zadanie 13

|Co	|trace: 'on'|	retain-on-failure|
|---|---|---|
|Rozmiar playwright-report|		13.7 MB | 	894 KB|
|Suma rozmiarów blob-report-*	|13.186 MB|	~400kB|


- czy zapytanie do API o produkty się powiodło i co zwróciło dla produktu p-012? - Tak, kod 200 i obiekt
- czy na stronie jest element z etykietą „Ostatnie sztuki”, czy go nie ma wcale? - nie ma
- skoro dane są takie, jakie są, a strona wygląda tak, jak wygląda — w którym miejscu kodu szukać przyczyny? - w lokatorach



