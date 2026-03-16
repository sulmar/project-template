# ADR-002 Wykorzystanie Redis jako warstwy cache

## Status

Proposed

---

## Kontekst

W miarę rozwoju projektu odczyt danych może stawać się coraz częstszy, a główna baza danych może zacząć obsługiwać zbyt dużo zapytań.

Taka sytuacja może dotyczyć między innymi:

- list zamówień,
- szczegółów zamówienia,
- danych tymczasowych wykorzystywanych przez aplikację.

Na obecnym etapie nie ma jeszcze potrzeby wprowadzania dodatkowej infrastruktury, ale taka decyzja może pojawić się w dalszym rozwoju systemu.

Rozważano dwa podejścia:

- brak warstwy cache,
- wykorzystanie Redis jako warstwy cache.

---

## Decyzja

Na obecnym etapie **nie wdrażamy Redis**, ale traktujemy go jako sensowną **propozycję** dla bardziej rozbudowanej wersji systemu.

Jeśli w kolejnych iteracjach pojawią się problemy wydajnościowe lub potrzeba przechowywania danych tymczasowych, Redis może zostać zaakceptowany jako osobna warstwa cache.

---

## Alternatywy

### Brak cache

System korzysta wyłącznie z głównej bazy danych.

Plusy:

- prostsza architektura,
- brak dodatkowej infrastruktury,
- łatwiejsze utrzymanie rozwiązania.

Minusy:

- większe obciążenie bazy danych,
- wolniejsze odczyty przy dużej liczbie zapytań.

### Redis

Dodatkowa warstwa cache oparta o Redis.

Plusy:

- bardzo szybki dostęp do danych,
- zmniejszenie obciążenia bazy danych,
- dobry przykład rozwiązania spotykanego w większych systemach.

Minusy:

- dodatkowa infrastruktura do utrzymania,
- większa złożoność architektury,
- konieczność przemyślenia strategii wygaszania i synchronizacji danych.

---

## Konsekwencje

Pozytywne:

- obecna architektura pozostaje prosta,
- decyzja jest udokumentowana z wyprzedzeniem,
- zespół ma gotowy punkt wyjścia do rozmowy o skalowaniu systemu.

Negatywne:

- obecna wersja systemu nie pokazuje implementacji cache,
- może być potrzebny osobny ADR lub aktualizacja tego dokumentu po rzeczywistym wdrożeniu Redis.
