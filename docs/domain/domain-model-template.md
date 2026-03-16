# Model domenowy

Ten dokument warto uzupełnić po opisaniu pierwszych przypadków użycia. Ma pomagać uchwycić obiekty domenowe i reguły biznesowe, a nie być tylko listą klas.

## Opis domeny

Krótki opis problemu biznesowego, który rozwiązuje system.

Przyklad:

System służy do zarządzania zamówieniami klientów w sklepie internetowym.

---

## Elementy modelu

### EntityName

Opis odpowiedzialności elementu domenowego.

Główne atrybuty:

- `Id`
- `Name`
- `Status`

Najważniejsze reguły biznesowe:

- reguła 1
- reguła 2

---

### AnotherEntity

Opis odpowiedzialności kolejnego elementu.

Główne atrybuty:

- `Id`
- `OrderId`
- `ProductId`
- `Quantity`

---

## Relacje

Opisz zależności pomiędzy encjami, value objects i enumami.

Przyklad:

- `Order` zawiera wiele `OrderItem`.
- `OrderItem` nalezy do jednego `Order`.

## Uwagi

Jeśli model jest jeszcze niepełny, warto to wprost zaznaczyć. Dokument ma odzwierciedlać aktualne rozumienie domeny, a nie udawać kompletne rozwiązanie.