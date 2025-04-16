# 🛎️ Zadania SQL — Triggery (Baza Chinook)

> 🗂️ **Rozwiązania zadań należy umieścić w pliku `triggers.sql` w katalogu `scripts/`.**

## 🔹 Zadanie 1 — Poziom prosty: Logowanie usunięcia klienta

**Opis:**
Stwórz trigger `LogCustomerDelete`, który:
- Reaguje na usunięcie klienta z tabeli `Customer` (akcja `DELETE`),
- Wstawia dane do nowej tabeli `DeletedCustomersLog`, która przechowuje informacje o usuniętych klientach.

**Tabela `DeletedCustomersLog` powinna zawierać:**
- `CustomerId`, `FirstName`, `LastName`, `Email`, `DeletedAt` (z bieżącą datą `NOW()`)

> 💡 **Uwaga:** Przetestuj trigger, usuwając klienta z przykładowymi danymi i sprawdź, czy log się utworzył.

---

## 🔶 Zadanie 2 — Poziom średni: Sprawdzenie kraju klienta przed aktualizacją

**Opis:**
Zaprojektuj trigger `CheckCustomerCountryChange`, który:
- Aktywuje się przed aktualizacją danych klienta (`BEFORE UPDATE`),
- Jeśli pole `Country` ma zostać zmienione na `USA`, a wcześniej było inne — zapisuje takie zdarzenie w tabeli `CountryChangeLog`.

**Tabela `CountryChangeLog` powinna zawierać:**
- `CustomerId`, `OldCountry`, `NewCountry`, `ChangedAt`

**Wymagania:**
- Zapisuj tylko zmiany na `USA`.
- Nie przerywaj operacji aktualizacji.

> 💡 **Uwaga:** Przetestuj trigger aktualizując `Country` kilku klientów z różnych krajów.

---

## 🔟 Zadanie 3 — Poziom zaawansowany: Walidacja długości utworu przy dodawaniu

**Opis:**
Zaprojektuj trigger `ValidateTrackLength`, który:
- Reaguje na dodanie nowego utworu do tabeli `Track` (`BEFORE INSERT`),
- Blokuje dodanie rekordu, jeśli długość utworu (`Milliseconds`) jest mniejsza niż 30 sekund (czyli `30000`).

**Wymagania:**
- Jeśli warunek nie jest spełniony, trigger powinien wywołać błąd za pomocą `SIGNAL SQLSTATE`.

> 💡 **Uwaga:** Przetestuj działanie triggera dodając utwory o różnych długościach, w tym poniżej 30 sekund.

---

**📆 Notatka:**
Triggery można rozbudować o dodatkowe warunki, ograniczenia i logikę związaną z audytem danych lub bezpieczeństwem.

