# Decyzje architektoniczne (ADR)

ADR (Architecture Decision Record) to krótki dokument opisujący decyzję architektoniczną w projekcie, np.:
- dlaczego wybrano Redis zamiast PostgreSQL do cache,
- dlaczego użyto gRPC zamiast REST,
- dlaczego wybrano RabbitMQ zamiast Kafka.

Typowy ADR zawiera:
- kontekst problemu,
- podjętą decyzję,
- konsekwencje tej decyzji (pozytywne i negatywne).

Każdy istotny wybór architektoniczny (technologia, protokół komunikacji, sposób integracji, struktura modułów itp.) powinien być opisany w osobnym pliku ADR w tym katalogu.

## Jak korzystać z ADR w tym projekcie

- Jeden plik odpowiada jednej decyzji.
- Nowy ADR twórz wtedy, gdy decyzja:
  - wpływa na architekturę systemu,
  - jest kosztowna do cofnięcia,
  - będzie ważna jako kontekst dla przyszłych zmian.
- Gdy decyzja się zmienia, dodaj nowy ADR, który opisze zmianę i wskaże, który wcześniejszy ADR zastępuje.

## Struktura pojedynczego ADR

Każdy ADR powinien zawierać co najmniej:
- **Status** – np. `Proposed`, `Accepted`, `Rejected`, `Deprecated`.
- **Kontekst** – opis problemu i ograniczeń,
- **Decyzję** – co dokładnie zostało ustalone,
- **Konsekwencje** – skutki decyzji (pozytywne i negatywne).

Dodatkowo można opisać:
- **Alternatywy** – jakie inne opcje były rozważane i dlaczego zostały odrzucone,

## Szablon ADR

Do tworzenia nowych decyzji możesz skorzystać z szablonu:

- `docs/decisions/adr-template.md`

Skopiuj jego zawartość do nowego pliku i uzupełnij zgodnie z opisanymi tam sekcjami.

## Konwencja nazewnictwa plików

Pliki ADR w tym projekcie nazywamy według schematu:

- `ADR-0001-use-minimal-api.md`
- `ADR-0002-use-cache-redis.md`
- `ADR-0003-opis-decyzji.md`

Zalecenia:
- numeruj kolejne decyzje rosnąco (`0001`, `0002`, `0003`, ...), aby zachować chronologię,
- w tytule po numerze używaj krótkiego, opisowego slug-a w języku angielskim lub polskim (np. `use-cache-redis`, `model-order-aggregate`),
- nie zmieniaj nazw istniejących plików ADR, żeby nie łamać odwołań w dokumentacji i historii zmian.