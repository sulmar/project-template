# Zarządzanie zamówieniami

Ten katalog opisuje niewielki, ale spójny system. Celem nie jest kompletna realizacja wszystkich funkcji, tylko pokazanie uporządkowanego fundamentu: od przypadku użycia i modelu domenowego po implementację i testy.

---

## Cel projektu

Szablon ma pokazać:

- podejście **Use Case Driven Development**,
- podstawy **modelowania domenowego**,
- prosty podział na warstwy w .NET,
- dokumentowanie decyzji projektowych,
- łączenie dokumentacji z kodem i testami.

---

## Aktualny zakres

Kod implementuje jeden referencyjny pionowy wycinek:

- **UC-01 Utworzenie zamówienia**

Drugi przypadek użycia w `docs/use-cases/UC02-cancel-order.md` został pozostawiony jako przykład dalszego rozwoju projektu.

---

## Jak czytać projekt

Najlepiej przejść po nim w tej kolejności:

1. `docs/use-cases/UC01-create-order.md`
2. `docs/domain/domain-model.md`
3. `docs/architecture/overview.md`
4. `docs/decisions/`
5. `src/` i `tests/`

Dzięki temu łatwo przejść od dokumentacji do implementacji.

---

## Architektura

Projekt wykorzystuje prosty podział na warstwy:

`API -> Application -> Domain`

Warstwa `Infrastructure` implementuje kontrakty potrzebne aplikacji, ale nie zawiera logiki biznesowej.

Szczegóły znajdują się w:

`docs/architecture/overview.md`

---

## Model domenowy

Główne elementy przykładu:

- `Order`
- `OrderItem`
- `OrderStatus`

Szczegóły znajdują się w:

`docs/domain/domain-model.md`

---

## Decyzje architektoniczne

Kluczowe decyzje projektowe są dokumentowane w katalogu:

`docs/decisions`

Dokumentacja obejmuje tylko decyzje bazowe. Bardziej zaawansowane elementy warto dodawać dopiero wtedy, gdy wynikają z realnych potrzeb.

---

## Uruchomienie projektu

### Wymagania

- .NET 10 SDK

### Przykladowe polecenia

```bash
dotnet restore ../ProjectTemplate.sln
dotnet build ../ProjectTemplate.sln
dotnet test ../ProjectTemplate.sln
dotnet run --project ../src/Api/ProjectTemplate.Api.csproj
```

---

## Zasady pracy

Przy pierwszych iteracjach warto pilnować zasady:

- najpierw use case,
- potem model i decyzje,
- potem test,
- na końcu implementacja.

