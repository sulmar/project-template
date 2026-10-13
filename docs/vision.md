# Wizja

## Problem

Nowy projekt .NET często startuje od struktury katalogów albo od frameworka. Wymaganie, model domenowy i kod rozjeżdżają się, zanim pojawi się pierwszy działający wycinek.

Ten szablon pokazuje inną kolejność: najpierw przypadek użycia i reguły zamówienia, potem decyzja, test i kod.

## Dla kogo

Dla zespołu, który zaczyna małą usługę HTTP w .NET i chce mieć czytelny punkt startowy.

Przykładem jest **Order Management Service**: klient tworzy zamówienie, system pilnuje jego danych i cyklu życia. Domena zamówień jest ilustracją. Właściwym produktem szablonu jest ścieżka od wymagania do kodu.

## Cel

Jedna, działająca ścieżka od przypadku użycia do testu, bez warstw dodanych na zapas.

W aktualnym wycinku klient tworzy zamówienie (`UC-01`). System zapisuje je ze statusem `Created`. Anulowanie (`UC-02`) jest opisane i częściowo obecne w modelu: wysłanego zamówienia nie wolno anulować. Endpoint anulowania jeszcze nie istnieje.

## Zasady

- Przypadek użycia opisuje zachowanie, zanim powstanie endpoint.
- Reguły biznesowe zostają w `Domain`. Warstwa aplikacji je wywołuje, infrastruktura ich nie zna.
- Decyzja trudna do cofnięcia trafia do ADR. Reszta zostaje w kodzie.
- Nowa technologia wchodzi wtedy, gdy obecny wycinek jej potrzebuje. Redis jest propozycją, nie częścią systemu.
- Test jest częścią wycinka: reguła domenowa ma test jednostkowy, endpoint ma test integracyjny.

## Zakres

W szablonie jest:

- utworzenie zamówienia przez `POST /orders`,
- agregat `Order` z pozycjami i statusem,
- repozytorium w pamięci,
- testy jednostkowe i integracyjne.

Poza aktualnym wycinkiem zostają:

- anulowanie zamówienia jako endpoint,
- ustawianie statusu `Shipped`,
- osobny katalog produktów,
- trwała baza danych i cache.

## Kierunek

Kolejny krok to dokończenie `UC-02` tą samą ścieżką: scenariusz, reguła w agregacie, test, potem endpoint. Trwała persystencja i cache pojawiają się dopiero wtedy, gdy odczyt albo zapis w pamięci przestaje wystarczać.

Szablon ma zostać mały. Rozrost oznacza kolejny przypadek użycia, nie kolejną warstwę.
