# 📝 Zadania SQL — Procedury Składowane (Baza Chinook)

> 🗂️ **Rozwiązania zadań należy umieścić w pliku `procedures.sql` w katalogu `scripts/`.**

## 🔹 Zadanie 1 — Poziom prosty: Dodaj nowego klienta

**Opis:**
Napisz procedurę o nazwie `AddCustomer`, która przyjmuje dane nowego klienta i wstawia je do tabeli `Customer`. Parametry wejściowe:
- `p_FirstName` VARCHAR(40)
- `p_LastName` VARCHAR(20)
- `p_Country` VARCHAR(40)
- `p_Email` VARCHAR(60)

**Wymagania:**
- Użyj instrukcji `INSERT INTO`.
- Zakładamy, że pozostałe dane nie są wymagane lub ustawione jako `NULL`.
- Dodaj sprawdzenie, czy klient o podanym e-mailu już istnieje. Jeśli tak, zakończ procedurę bez dodawania wpisu.

> 💡 **Uwaga:** Przygotuj zapytanie testowe, które wywołuje procedurę z przykładowymi danymi, aby sprawdzić jej działanie.

---

## 🔶 Zadanie 2 — Poziom średni: Aktualizacja ilości utworów zakupionych przez klienta

**Opis:**
Stwórz procedurę o nazwie `UpdateCustomerInvoiceStats`, która:
- Przelicza sumaryczną wartość zakupów klienta oraz liczbę utworów (Track) dla wszystkich faktur klienta (`Invoice`),
- Aktualizuje te informacje w nowej tabeli statystycznej o nazwie `CustomerStats` (tę tabelę trzeba najpierw stworzyć).

**Tabela `CustomerStats` powinna zawierać:**
- `CustomerId` (PK)
- `TotalInvoices` INT
- `TotalTracksPurchased` INT
- `TotalAmountSpent` DECIMAL(10,2)

**Wymagania:**
- Jeśli klient nie ma żadnej faktury, wpisz zera.
- Jeśli klient nie istnieje w tabeli `CustomerStats`, wstaw nowy rekord. W przeciwnym razie zaktualizuj istniejący.

> 🔍 **Uwaga:** Tabelę `CustomerStats` można stworzyć na podstawie danych wynikowych komendy `SELECT`, używając polecenia `CREATE TABLE CustomerStats AS SELECT ...`.

> 💡 **Uwaga:** Przygotuj zapytanie testowe, które wykonuje procedurę z przykładowym `CustomerId`.

---

## 🔟 Zadanie 3 — Poziom zaawansowany: Lista ulubionych gatunków klienta

**Opis:**
Stwórz procedurę `GetCustomerFavoriteGenres`, która:
- Przyjmuje `CustomerId` jako parametr wejściowy,
- Zwraca tabelę z gatunkami muzycznymi (`Genre.Name`), które najczęściej pojawiają się w zakupionych przez klienta utworach,
- Uwzględnia tylko utwory zrealizowane w fakturach (`Invoice`) przypisanych do danego klienta.

**Wymagania:**
- Skorzystaj z połączeń między tabelami: `Customer` → `Invoice` → `InvoiceLine` → `Track` → `Genre`.
- Zastosuj grupowanie oraz funkcję agregującą `COUNT(*)`.
- Posortuj wynik malejąco według liczby wystąpień.

> 💡 **Uwaga:** Przygotuj testowe zapytanie wykonujące procedurę z przykładowym identyfikatorem klienta, aby upewnić się, że działa zgodnie z oczekiwaniami.

---

**📆 Notatka:**
Każde zadanie może być rozszerzone przez dodanie dodatkowych warunków lub bardziej zaawansowanej logiki po wykonaniu wersji podstawowej. Zachęcamy do przygotowania scenariuszy testowych!

