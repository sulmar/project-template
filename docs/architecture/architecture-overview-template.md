# Przegląd architektury

Ten dokument uzupełnij, gdy zespół rozumie już pierwsze przypadki użycia i podjął podstawowe decyzje o strukturze projektu.

## Styl architektury

Opisz wybrane podejście, np. prosty podział warstwowy lub lekką Clean Architecture.

Warstwy:

- API
- Application
- Domain
- Infrastructure

## Diagram zależności

Pokaż, kto od kogo zależy. W szczególności dopilnuj, aby opis i diagram nie były ze sobą sprzeczne.

Przyklad:

`Client -> Api -> Application -> Domain`

`Api -> Infrastructure`

`Infrastructure -> Application`

## Opis warstw

### API

Odpowiada za komunikację z klientem i mapowanie żądań na przypadki użycia.

### Application

Zawiera logikę aplikacyjną i przepływy use case.

Przyklady:

- handlery,
- komendy,
- modele odpowiedzi,
- kontrakty repozytoriów.

### Domain

Zawiera model domenowy i reguły biznesowe.

Przyklady:

- encje,
- value objects,
- enumy,
- metody pilnujące invariantów.

### Infrastructure

Zawiera szczegóły techniczne.

Przyklady:

- baza danych,
- repozytoria,
- integracje zewnętrzne.

## Uwagi

Jeśli projekt jest dopiero na początku, opisz architekturę na tyle, by prowadziła zespół, ale nie dokładaj elementów, których jeszcze realnie nie potrzebujecie.
