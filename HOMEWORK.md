# 🏠 Zadania domowe

> 🗂️ **Rozwiązania zadań należy umieścić w odpowiednich plikach (`procedures_homework.sql`, `functions_homework.sql`, `triggers_homework.sql`) w katalogu `scripts/`.**

---

## 🔧 Procedury

### 🔹 Zadanie 1: Automatyczne przypisanie opiekuna do klienta

**Opis:**
Stwórz procedurę `AssignSupportRepToCustomer`, która:
- Przyjmuje `CustomerId` i `SupportRepId`,
- Przypisuje danego opiekuna (`EmployeeId`) do klienta (aktualizacja pola `SupportRepId` w tabeli `Customer`),
- Sprawdza, czy podany `EmployeeId` istnieje i ma stanowisko `'Support Agent'`.

> 💡 **Uwaga:** Przygotuj testowe dane klientów i pracowników, by sprawdzić poprawność działania procedury.

---

### 🔹 Zadanie 2: Aktualizacja typu pliku w zależności od rozszerzenia

**Opis:**
Napisz procedurę `UpdateMediaTypeByExtension`, która:
- Iteruje po wszystkich rekordach w tabeli `Track`,
- Na podstawie rozszerzenia pliku (`Name` pola Track, np. `.mp3`, `.wav`) przypisuje odpowiednie `MediaTypeId`.

> 💡 **Uwaga:** Zadbaj o obsługę kilku typowych rozszerzeń oraz przygotuj testowy zestaw utworów.

---

## 🧠 Funkcje

### 🔸 Zadanie 3: Średnia cena utworów w albumie

**Opis:**
Napisz funkcję `GetAverageTrackPriceForAlbum`, która:
- Przyjmuje `AlbumId`,
- Zwraca średnią cenę wszystkich utworów z danego albumu (na podstawie `InvoiceLine.UnitPrice`).

> 💡 **Uwaga:** Zadbaj o sytuacje, gdy album nie był jeszcze nigdy kupiony.

---

### 🔸 Zadanie 4: Klient premium

**Opis:**
Stwórz funkcję `IsPremiumCustomer`, która:
- Zwraca `1`, jeśli klient wydał więcej niż 100 dolarów, w przeciwnym razie `0`.
- Przyjmuje `CustomerId` jako parametr.

> 💡 **Uwaga:** Wykorzystaj sumę wartości z `Invoice.Total` i zadbaj o brak faktur.

---

## 🛎️ Triggery

### 🔻 Zadanie 5: Zabezpieczenie przed usunięciem utworu z fakturą

**Opis:**
Zaprojektuj trigger `PreventTrackDeleteIfInInvoice`, który:
- Blokuje usunięcie rekordu z tabeli `Track`, jeżeli ten utwór występuje w tabeli `InvoiceLine`.

> 💡 **Uwaga:** Użyj `BEFORE DELETE` i `SIGNAL SQLSTATE`, by poinformować użytkownika.

---

### 🔻 Zadanie 6: Automatyczny wpis do logu zmian cen

**Opis:**
Stwórz trigger `LogTrackPriceChange`, który:
- Działa przy zmianie ceny utworu (`UnitPrice` w tabeli `Track`),
- Dodaje wpis do tabeli `TrackPriceLog` zawierający: `TrackId`, `OldPrice`, `NewPrice`, `ChangedAt`.

> 💡 **Uwaga:** Zadbaj, by log tworzony był tylko, gdy cena faktycznie się zmieniła.

---

**📆 Notatka:**
Zadania domowe mogą wymagać dodatkowego testowania i tworzenia danych. Zachęcam do dokumentowania przyjętych założeń!
