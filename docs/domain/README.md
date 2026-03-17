## Model domenowy (domain)

Model domenowy opisuje **język i pojęcia biznesowe** używane w systemie, np.:
- jakie mamy agregaty i encje (np. `Order`, `Customer`),
- jakie reguły biznesowe rządzą ich zachowaniem,
- jakie są ograniczenia i inwarianty.

Typowy dokument w tym folderze zawiera:
- **słownik pojęć domenowych**,
- **diagramy lub opisy agregatów i relacji**,
- **reguły biznesowe** powiązane z konkretnymi obiektami domenowymi.

To miejsce, w którym opisujesz „o czym jest system” niezależnie od technologii i szczegółów implementacyjnych. Dokumenty z tego katalogu są bezpośrednim punktem odniesienia dla warstwy `Domain` w kodzie.

