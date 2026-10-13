# Słownik pojęć

Wspólny język tego szablonu. Hasła opisują to, co jest w dokumentacji i w kodzie, a nie ogólny podręcznik.

Szerszy opis obiektów jest w [modelu domenowym](domain/domain-model.md), przepływ w [przeglądzie architektury](architecture/overview.md).

## Domena

### Agregat

Obiekt domenowy, który pilnuje spójności swoich części. `Order` jest agregatem: pozycje i status zmieniają się tylko przez jego operacje.

### Klient

Aktor, który tworzy i anuluje zamówienie. W modelu nie ma osobnej encji klienta. Zamówienie trzyma wyłącznie `CustomerId`.

### Order

Agregat zamówienia. `Order.Create` buduje zamówienie ze statusem `Created`. `Order.Cancel()` zmienia status na `Cancelled`, o ile zamówienie nie jest wysłane.

### OrderItem

Jedna pozycja zamówienia: `ProductId`, `Quantity` i `UnitPrice`. Osobnego katalogu produktów nie ma. Cena zostaje zapisana na pozycji.

### OrderStatus

Stan zamówienia.

- `Created` — status nadawany przy utworzeniu.
- `Cancelled` — status po `Cancel()`. Kolejne anulowanie zostawia ten sam status.
- `Shipped` — zamówienie wysłane. `Cancel()` odrzuca ten stan. Żadna metoda jeszcze go nie ustawia.

### Reguła biznesowa

Ograniczenie, które zostaje w `Domain`. Zamówienie musi mieć klienta i co najmniej jedną pozycję. Ilość i cena pozycji muszą być większe od zera. Wysłanego zamówienia nie wolno anulować.

## Przypadki użycia

### Aktor

Osoba albo system, który uruchamia scenariusz. W tym szablonie aktorem jest klient.

### Pionowy wycinek

Jedna ścieżka od przypadku użycia przez regułę, test i kod. Aktualny wycinek to `UC-01`: endpoint, handler, agregat, repozytorium w pamięci i testy.

### Przypadek użycia

Opis zachowania systemu z punktu widzenia aktora, zapisany zanim powstanie endpoint. Zawiera aktora, warunki wstępne, scenariusz i rezultat.

## Architektura

### ADR

Architecture Decision Record. Zapis decyzji trudnej do cofnięcia: kontekst, decyzja, konsekwencje. `Proposed` oznacza propozycję, `Accepted` decyzję obowiązującą. Zmianę opisuje nowy ADR. Zasady są w [katalogu decyzji](decisions/README.md).

### API

Warstwa HTTP. Wystawia endpointy, mapuje żądanie na przypadek użycia i składa zależności.

### Application

Warstwa przypadków użycia: komenda, handler i kontrakt repozytorium. Woła `Domain` i nie zna sposobu zapisu.

### Clean Architecture

Podział, w którym reguły biznesowe nie zależą od HTTP ani od sposobu zapisu. `Domain` nie odwołuje się do `Infrastructure`.

### Domain

Warstwa modelu i reguł: `Order`, `OrderItem` i `OrderStatus`.

### Endpoint

Adres HTTP przypadku użycia. Działa `POST /orders`. `DELETE /orders/{id}` jest tylko w opisie `UC-02`.

### Handler

Klasa, która wykonuje jeden przypadek użycia. `CreateOrderHandler` woła `Order.Create` i zapisuje wynik przez `IOrderRepository`.

### Infrastructure

Warstwa szczegółów technicznych. Dziś jest tu `InMemoryOrderRepository`.

### Komenda

Dane wejściowe handlera, na przykład `CreateOrderCommand`.

### Minimal API

Sposób definiowania endpointów w ASP.NET Core bez kontrolerów. Obowiązuje na mocy [ADR-001](decisions/ADR-001-use-minimal-api.md).

### Redis

Propozycja warstwy cache z [ADR-002](decisions/ADR-002-use-cache-redis.md). Nie jest częścią działającego systemu.

### Repozytorium

Kontrakt odczytu i zapisu agregatu. `IOrderRepository` leży w `Application`. Implementacja w pamięci leży w `Infrastructure`.

### Test integracyjny

Sprawdza endpoint razem ze złożeniem aplikacji.

### Test jednostkowy

Sprawdza regułę w `Domain`, bez HTTP i bez repozytorium.
