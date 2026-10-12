# Dokumentacja projektu

## Przypadki uzycia
docs/use-cases

## Architektura
docs/architecture

## Model domenowy
docs/domain

## Decyzje architektoniczne
- docs/decisions

## Diagramy UML stosowane w dokumentacji

- [Mapa przypadków użycia](use-cases/README.md#mapa-przypadków-użycia)
- [Diagram sekwencji, UC-01](use-cases/UC01-create-order.md#diagram-sekwencji)
- [Diagram sekwencji, UC-02](use-cases/UC02-cancel-order.md#diagram-sekwencji)
- [Diagram klas](domain/domain-model.md#diagram-klas)
- [Diagram stanów](domain/domain-model.md#diagram-stanów)
- [Diagram zależności](architecture/overview.md#diagram-zależności)
- [Diagram komponentów](architecture/overview.md#diagram-komponentów)
- [Mapowanie dokumentacji na kod](architecture/overview.md#mapowanie-dokumentacji-na-kod)

## W jaki sposób wygenerować diagram w formacie mermaid w postaci PDF
Zakładając, że masz zainstalowany **Node.js** oraz plik **`plik.md`** z diagramem:

1. **Zainstaluj narzędzie `mmdc` globalnie:**

```bash
npm install -g @mermaid-js/mermaid-cli
```

2. **Wygeneruj PDF z diagramu:**

```bash
mmdc -i plik.md -o diagram.pdf
```


## Kiedy dodać diagram

Wystarczy pięć diagramów. Każdy pojawia się wtedy, gdy tekst przestaje pokazywać relację, przepływ albo regułę.

| Diagram | Kiedy | Gdzie w tym projekcie |
|---|---|---|
| Przypadków użycia | Na starcie, gdy jest więcej niż jeden scenariusz i trzeba pokazać aktorów oraz zakres systemu | `docs/use-cases/README.md` |
| Sekwencji | Przy konkretnym przypadku użycia, gdy żądanie idzie przez kilka warstw: API, handler, agregat, repozytorium | plik danego UC, np. `docs/use-cases/UC01-create-order.md` |
| Klas | Gdy model domenowy się ustala: agregaty, atrybuty, operacje i relacje | `docs/domain/domain-model.md` |
| Stanów | Gdy obiekt ma cykl życia i część przejść jest zabroniona, jak anulowanie wysłanego zamówienia | obok diagramu klas, przy regułach biznesowych |
| Komponentów | Gdy opisujesz budowę systemu: warstwy, zależności i to, co naprawdę jest w kodzie | `docs/architecture/overview.md` |

Kolejność wynika z workflow szablonu. Najpierw mapa przypadków użycia, potem sekwencja dla scenariusza, który wchodzi do implementacji. Diagram klas i stanów powstają razem z modelem domenowym. Diagram komponentów na końcu, gdy widać już warstwy i pierwszy pionowy wycinek.

ADR zostaje tekstem: kontekst, decyzja, konsekwencje. Diagram ma sens dopiero wtedy, gdy decyzja zmienia układ komponentów, na przykład po przyjęciu cache.