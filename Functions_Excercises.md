# 🧠 Zadania SQL — Funkcje Użytkownika (Baza Chinook)

> 🗂️ **Rozwiązania zadań należy umieścić w pliku `functions.sql` w katalogu `scripts/`.**

## 🔹 Zadanie 1 — Poziom prosty: Oblicz długość utworu w minutach

**Opis:**
Napisz funkcję `GetTrackLengthInMinutes`, która:
- Przyjmuje identyfikator utworu (`TrackId` INT),
- Zwraca jego długość w minutach jako wartość typu `DECIMAL(5,2)` (na podstawie pola `Milliseconds` z tabeli `Track`).

**Wymagania:**
- Wykonaj konwersję z milisekund do minut (`Milliseconds / 60000`).
- Zadbaj o zaokrąglenie wyniku do dwóch miejsc po przecinku.

> 💡 **Uwaga:** Przetestuj funkcję dla kilku utworów o różnych długościach.

---

## 🔶 Zadanie 2 — Poziom średni: Czy klient jest aktywny?

**Opis:**
Zaprojektuj funkcję `IsActiveCustomer`, która:
- Przyjmuje `CustomerId` jako parametr,
- Zwraca `1` jeśli klient ma przynajmniej jedną fakturę (`Invoice`), lub `0` w przeciwnym przypadku.

**Wymagania:**
- Użyj podzapytania z `EXISTS` lub `COUNT`.
- Typ zwracany: `TINYINT(1)`.

> 💡 **Uwaga:** Przetestuj funkcję zarówno na aktywnym, jak i nieaktywnym kliencie.

---

## 🔟 Zadanie 3 — Poziom zaawansowany: Całkowity czas trwania zakupionych utworów

**Opis:**
Stwórz funkcję `GetTotalListeningTime`, która:
- Przyjmuje `CustomerId`,
- Zwraca całkowity czas trwania wszystkich zakupionych przez klienta utworów w minutach (typu `DECIMAL(10,2)`).

**Wymagania:**
- Połącz odpowiednie tabele: `Customer` → `Invoice` → `InvoiceLine` → `Track`.
- Zsumuj pole `Milliseconds`, przelicz je na minuty.

> 💡 **Uwaga:** Sprawdź działanie funkcji dla klienta z wieloma zakupami oraz klienta bez żadnych faktur.

---

**📆 Notatka:**
Każdą funkcję warto rozbudować o dodatkowe walidacje lub wersje przyjmujące inne parametry. Zachęcamy do kreatywnego podejścia!

