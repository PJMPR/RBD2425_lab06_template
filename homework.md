# Praca domowa – Zaawansowane operacje SQL (Chinook)

Poniższe zadania domowe mają na celu sprawdzenie zaawansowanej znajomości komend SQL w kontekście pracy z relacyjną bazą danych Chinook. Każde zadanie dotyczy jednej z kluczowych komend SQL: `CREATE TABLE`, `INSERT`, `DELETE`, `UPDATE`, `CREATE VIEW`.

> 🧪 **Uwaga:** Jeśli zapytania `SELECT` w zadaniach nie zwracają wyników, dodaj odpowiednie dane testowe za pomocą `INSERT`, aby móc poprawnie wykonać zadanie.

---

## 🔸 Zadanie 1 – `CREATE TABLE`: Historia zakupów utworów

**Cel:** Utworzyć tabelę przechowującą historię zakupów utworów przez klientów wraz z dodatkowymi metadanymi.

### 📝 Struktura tabeli `TrackPurchaseHistory`:
| Kolumna         | Typ danych     | Opis                                       |
|------------------|----------------|--------------------------------------------|
| HistoryId        | INT            | Klucz główny AUTO_INCREMENT                |
| CustomerId       | INT            | ID klienta                                 |
| TrackId          | INT            | ID utworu                                  |
| PurchaseDate     | DATETIME       | Data zakupu                                |
| PurchaseAmount   | DECIMAL(10,2)  | Kwota transakcji                           |
| PaymentMethod    | VARCHAR(50)    | Metoda płatności (np. Credit Card, PayPal) |

### ✅ Zadania do wykonania:
- Utwórz powyższą tabelę.
- Zaplanuj użycie tej tabeli w dalszych analizach zakupowych klientów.

---

## 🔸 Zadanie 2 – `INSERT`: Zasilanie historii zakupów

**Cel:** Na podstawie istniejących danych wstawić rekordy do tabeli `TrackPurchaseHistory`.

### ✅ Zadania do wykonania:
1. Przygotuj zapytanie `SELECT`, które pobiera dane klientów, utworów, daty faktur i kwot z tabel `Invoice`, `InvoiceLine`, `Customer`, `Track`.
2. Wykorzystaj `INSERT INTO ... SELECT ...`, aby zasilić nową tabelę `TrackPurchaseHistory`.
3. Dodaj fikcyjne dane w kolumnie `PaymentMethod` (np. ustaw ją jako `'Credit Card'` dla wszystkich rekordów).

---

## 🔸 Zadanie 3 – `DELETE`: Czyszczenie rekordów z błędną płatnością

**Cel:** Usunąć z tabeli `TrackPurchaseHistory` rekordy z niewłaściwym oznaczeniem metody płatności.

### ✅ Zadania do wykonania:
1. Przygotuj `SELECT`, które wyświetla wszystkie rekordy z `PaymentMethod` ustawionym na wartość `'Unknown'`.
2. Usuń te rekordy z tabeli.
3. Potwierdź usunięcie poprzez ponowne zapytanie `SELECT`.

---

## 🔸 Zadanie 4 – `UPDATE`: Korekta danych płatności

**Cel:** Skorygować metodę płatności na podstawie klienta lub kraju.

### ✅ Zadania do wykonania:
1. Zidentyfikuj klientów z Kanady (`Country = 'Canada'`), którzy mają w tabeli `TrackPurchaseHistory` metodę płatności ustawioną na `'Credit Card'`.
2. Zaktualizuj te rekordy i ustaw `PaymentMethod = 'Interac'`.
3. Wyświetl zaktualizowane dane, aby potwierdzić poprawność zmian.

---

## 🔸 Zadanie 5 – `CREATE VIEW`: Widok podsumowania wydatków

**Cel:** Stworzyć widok zawierający sumaryczne dane o wydatkach klientów.

### ✅ Zadania do wykonania:
1. Utwórz widok `CustomerSpendingSummary`, który zawiera:
   - `CustomerId`
   - `TotalSpent` (suma `PurchaseAmount`)
   - `TransactionsCount` (liczba rekordów zakupów)
2. Wykorzystaj dane z tabeli `TrackPurchaseHistory`.
3. Wykonaj zapytanie `SELECT * FROM CustomerSpendingSummary ORDER BY TotalSpent DESC LIMIT 10`.

---

> 📌 **Na koniec:** Zadbaj o poprawność nazw kolumn, typów danych i relacji między tabelami. Przed wykonaniem `DELETE` lub `UPDATE`, zawsze przetestuj warunek `SELECT`, aby uniknąć przypadkowego usunięcia danych.

