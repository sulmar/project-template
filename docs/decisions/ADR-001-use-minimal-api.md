# ADR-001 Wybór technologii warstwy API

## Status

Accepted

---

## Kontekst

System wymaga warstwy API umożliwiającej komunikację z klientem poprzez HTTP.

W projekcie ważne są:

- prostota implementacji
- mała ilość kodu konfiguracyjnego
- szybkie rozpoczęcie pracy nad funkcjonalnościami

Rozważano dwa podejścia dostępne w platformie .NET:

- ASP.NET Core MVC (Controllers)
- ASP.NET Core Minimal API

---

## Decyzja

Projekt wykorzystuje **ASP.NET Core Minimal API** jako warstwę API.

Minimal API pozwala definiować endpointy HTTP w prosty sposób, bez konieczności tworzenia kontrolerów i dodatkowej konfiguracji. Dobrze wspiera niewielki system, w którym liczy się szybkie dostarczanie funkcjonalności przy zachowaniu czytelności.

---

## Alternatywy

### ASP.NET Core MVC

Klasyczne podejście oparte na kontrolerach.

Plusy:

- dobrze znany wzorzec
- czytelna struktura kontrolerów
- szerokie wsparcie w ekosystemie

Minusy:

- więcej kodu szablonowego
- większa złożoność dla małego projektu
- wolniejsze rozpoczęcie implementacji

### ASP.NET Core Minimal API

Nowoczesne podejście wprowadzone w .NET 6.

Plusy:

- bardzo mała ilość kodu
- szybkie tworzenie endpointów
- dobre dopasowanie do niewielkich projektów i prostych usług

Minusy:

- mniejsza strukturalność w dużych projektach
- przy rozbudowie systemu może być potrzebne przejście do bardziej formalnej struktury

---

## Konsekwencje

Pozytywne:

- prostsza implementacja endpointów
- mniejsza ilość kodu
- szybsze rozpoczęcie pracy nad funkcjonalnościami

Negatywne:

- w przyszłości może być potrzebna refaktoryzacja przy rozbudowie systemu
- mniejsza strukturalność niż w przypadku MVC