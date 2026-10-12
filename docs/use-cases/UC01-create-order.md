# UC-01 Utworzenie zamówienia

## Aktor

Klient

## Opis

Klient tworzy nowe zamówienie w systemie.

## Warunki wstępne

- klient przekazuje poprawny `CustomerId`,
- zamówienie zawiera co najmniej jedną pozycję,
- każda pozycja ma `ProductId`, dodatnią ilość i dodatnią cenę.

## Główny scenariusz

1. Klient wybiera produkty do zamówienia.
2. Klient wysyła żądanie utworzenia zamówienia.
3. System waliduje dane wejściowe.
4. System tworzy agregat zamówienia.
5. System zapisuje zamówienie przez repozytorium.
6. System zwraca identyfikator i status nowego zamówienia.

## Rezultat

Zamówienie zostaje zapisane w systemie ze statusem `Created`.

## Diagram sekwencji

Przepływ zaimplementowany w `POST /orders`.

```mermaid
sequenceDiagram
    actor Klient
    participant API as "POST /orders"
    participant Handler as CreateOrderHandler
    participant Order
    participant Repo as IOrderRepository

    Klient->>API: customerId, items
    API->>Handler: CreateOrderCommand
    Handler->>Order: Create(customerId, items, utcNow)
    alt CustomerId pusty, brak pozycji, ilość lub cena mniejsza lub równa 0
        Order-->>Handler: ArgumentException
        Handler-->>API: wyjątek
        API-->>Klient: ValidationProblem
    else dane poprawne
        Order-->>Handler: Order, status Created
        Handler->>Repo: AddAsync(order)
        Repo-->>Handler: zapis
        Handler-->>API: CreateOrderResult
        API-->>Klient: 201 Created
    end
```

## API

`POST /orders`

Przykładowe pola żądania:

- `customerId`
- `items[].productId`
- `items[].quantity`
- `items[].unitPrice`

## Uwagi

To jest przypadek użycia zaimplementowany w aktualnej wersji systemu.