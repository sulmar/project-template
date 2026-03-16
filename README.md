# Order Management Service

*Ten szablon projektu pokazuje w prosty i praktyczny sposób, jak zaprojektować aplikację zgodnie z zasadami **Clean Architecture**, zaczynając od przypadków użycia i modelu domenowego, a kończąc na implementacji i testach.*

**Order Management Service** to prosta usługa HTTP do obsługi zamówień klientów. System pozwala utworzyć zamówienie, przechowuje jego podstawowe dane oraz utrzymuje reguły biznesowe związane z cyklem życia zamówienia. Projekt łączy dokumentację architektoniczną, model domenowy, implementację aplikacyjną i testy, tak aby cała ścieżka od wymagania do kodu była czytelna i spójna.

Repozytorium pokazuje spójny punkt startowy dla projektu .NET:

- dokumentacja prowadzi od problemu do decyzji projektowych,
- kod zawiera minimalny pionowy wycinek funkcjonalności,
- testy są elementem podstawowego workflow.

## Stos technologiczny

- `.NET 10`
- `ASP.NET Core Minimal API`
- `xUnit`
- repozytorium `in-memory`
- `GitHub Actions`

## Uruchomienie

Uruchamiaj polecenia z katalogu `project-template`:

```bash
dotnet restore ProjectTemplate.sln
dotnet build ProjectTemplate.sln
dotnet test ProjectTemplate.sln
dotnet run --project src/Api/ProjectTemplate.Api.csproj
```


## Struktura

```text
src/
  Api/             minimal API i kompozycja zależności
  Application/     przypadki użycia i kontrakty
  Domain/          model domenowy i reguły biznesowe
  Infrastructure/  szczegóły techniczne
docs/
  use-cases/       scenariusze funkcjonalne
  architecture/    opis struktury systemu
  domain/          model domenowy
  decisions/       ADR-y
tests/
  UnitTests/       szybkie testy logiki
  IntegrationTests/ testy endpointów i składania aplikacji
```

## Sugerowany workflow dla zespołu

1. Opisz przypadek użycia.
2. Ustal model domenowy i ogranicz zakres pierwszej implementacji.
3. Zapisz istotne decyzje w ADR.
4. Dodaj test jednostkowy lub integracyjny.
5. Dopiero potem rozwijaj kod produkcyjny.

## Autorzy

Do uzupełnienia.

## Licencja

Projekt jest udostępniany na licencji `MIT`, która pozwala na swobodne używanie, modyfikowanie i rozpowszechnianie oprogramowania przy zachowaniu informacji o autorstwie i licencji.
