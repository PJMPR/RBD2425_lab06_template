
# 📦 **Baza danych Chinook**  

Zadania w tym repozytorium oparte są na przykładowej bazie danych **Chinook**, która symuluje środowisko sklepu muzycznego online. Baza zawiera dane o klientach, pracownikach, utworach, albumach, fakturach oraz wykonawcach. Jest to popularny zbiór danych wykorzystywany do nauki SQL i relacyjnych baz danych.

Więcej informacji o projekcie Chinook można znaleźć tutaj: [https://github.com/lerocha/chinook-database](https://github.com/lerocha/chinook-database)


### Data Model
<img width="836" alt="image" src="https://github.com/lerocha/chinook-database/assets/135025/cea7a05a-5c36-40cd-84c7-488307a123f4">
---

# Zadania laboratoryjne – Tworzenie tabel w bazie danych Chinook

W poniższych zadaniach wykorzystaj znajomość poleceń `CREATE TABLE`, `SELECT`, `JOIN`, `ORDER BY` oraz funkcji agregujących. Każde zadanie wymaga stworzenia nowej tabeli na podstawie danych już istniejących w bazie Chinook.

---

## 🔹 Zadanie 1 – Log aktywności klientów 

**Cel:** Utworzyć tabelę zawierającą podstawowe informacje o aktywności klientów.

### 📝 Struktura tabeli `CustomerActivityLog`:
| Kolumna           | Typ danych        | Opis                                 |
|-------------------|-------------------|--------------------------------------|
| LogId             | INT AUTO_INCREMENT| Klucz główny                         |
| CustomerId        | INT               | ID klienta                           |
| FullName          | VARCHAR(200)      | Imię i nazwisko klienta              |
| TotalSpent        | DECIMAL(10,2)     | Łączna kwota wydana przez klienta    |
| LastPurchaseDate  | DATETIME          | Data ostatniego zakupu               |

### ✅ Zadania do wykonania:
1. Przygotuj zapytanie `SELECT`, które pobiera dane z tabel `Customer` i `Invoice`, agregując dane per klient.
2. Na podstawie tego zapytania utwórz nową tabelę `CustomerActivityLog` za pomocą konstrukcji `CREATE TABLE ... AS SELECT ...` (bez użycia `INSERT INTO`).
3. Wyświetl dane z tabeli `CustomerActivityLog`, posortowane malejąco według kolumny `TotalSpent`.

---

## 🔸 Zadanie 2 – Statystyki utworów według gatunku

**Cel:** Utworzyć tabelę raportową zawierającą statystyki dla każdego gatunku muzycznego.

### 📝 Struktura tabeli `GenreTrackStats`:
| Kolumna        | Typ danych      | Opis                                      |
|----------------|------------------|-------------------------------------------|
| GenreId        | INT              | ID gatunku                                |
| GenreName      | VARCHAR(120)     | Nazwa gatunku                             |
| NumberOfTracks | INT              | Liczba utworów w danym gatunku            |
| AverageDuration| DECIMAL(10,2)    | Średni czas trwania utworu (w sekundach)  |

### ✅ Zadania do wykonania:
1. Utwórz tabelę `GenreTrackStats` zgodnie z powyższą strukturą.
2. Korzystając z tabel `Genre` i `Track`, przygotuj zapytanie `SELECT`, które policzy liczbę utworów i ich średni czas trwania dla każdego gatunku.
3. Wstaw dane do tabeli `GenreTrackStats`.
4. Wyświetl tylko te rekordy, gdzie `NumberOfTracks` jest większe niż 100.

---

> 💡 **Wskazówka:** Upewnij się, że tabele mają poprawnie zdefiniowane klucze główne i typy danych odpowiadające danym źródłowym. W zadaniu 2 warto użyć `GROUP BY` oraz `HAVING`.


---

# Zadania laboratoryjne – INSERT + SELECT

W poniższych zadaniach wykorzystaj `INSERT` w połączeniu z `SELECT` do wstawiania danych w bazie Chinook. Zanim wykonasz dodanie, zawsze sprawdź dane przy pomocy `SELECT`, aby upewnić się, że chcesz dodac właściwe rekordy.

> 🧪 **Uwaga:** Jeśli Twoje zapytanie `SELECT` nie zwraca wyników, dodaj kilka własnych rekordów testowych do tabeli, aby móc zrealizować zadanie.

---

## 🔹 Zadanie 1 – Artyści bez albumów

**Cel:** Zidentyfikować artystów, którzy nie posiadają żadnych albumów, i umieścić ich w osobnej tabeli.

### 📝 Struktura tabeli `ArtistsWithoutAlbums`:
| Kolumna    | Typ danych    | Opis                     |
|------------|----------------|--------------------------|
| ArtistId   | INT            | ID artysty               |
| Name       | VARCHAR(120)   | Nazwa artysty            |

### ✅ Zadania do wykonania:
1. Utwórz tabelę `ArtistsWithoutAlbums` zgodnie z powyższą strukturą.
2. Za pomocą zapytania `SELECT` z `LEFT JOIN` znajdź artystów, którzy nie mają przypisanego żadnego albumu (jesli takich nie ma, to dodaj kilku testowych).
3. Wstaw dane do nowej tabeli za pomocą `INSERT INTO ... SELECT ...`.
4. Wyświetl wszystkich artystów znajdujących się w tabeli `ArtistsWithoutAlbums`.

---

## 🔸 Zadanie 2 – Klienci premium

**Cel:** Wyodrębnić klientów, którzy wydali powyżej 100 USD na zakupy i wprowadzić ich do osobnej tabeli.

### 📝 Struktura tabeli `PremiumCustomers`:
| Kolumna        | Typ danych     | Opis                                      |
|----------------|----------------|-------------------------------------------|
| CustomerId     | INT            | ID klienta                                |
| FullName       | VARCHAR(200)   | Imię i nazwisko                           |
| Country        | VARCHAR(100)   | Kraj klienta                              |
| TotalSpent     | DECIMAL(10,2)  | Łączna kwota wydana przez klienta         |

### ✅ Zadania do wykonania:
1. Utwórz tabelę `PremiumCustomers` zgodnie z powyższą strukturą.
2. Przygotuj zapytanie `SELECT`, które oblicza sumę zakupów klientów i wybiera tylko tych, którzy wydali więcej niż 100 USD.
3. Wstaw dane do nowej tabeli za pomocą `INSERT INTO ... SELECT ...`.
4. Wyświetl dane z tabeli `PremiumCustomers`, posortowane malejąco według `TotalSpent`.

---

> 💡 **Wskazówka:** Przy zadaniach z `INSERT` upewnij się, że wszystkie wymagane kolumny są uwzględnione, a typy danych zgodne z definicjami tabeli. Warto wcześniej sprawdzić, jakie wartości są dopuszczalne w kolumnach typu `Foreign Key` (np. `MediaTypeId`, `GenreId`).


# Zadania laboratoryjne – UPDATE + SELECT w bazie Chinook

W poniższych zadaniach wykorzystaj `UPDATE` w połączeniu z `SELECT` do aktualizacji danych w bazie Chinook. Zanim wykonasz aktualizację, zawsze sprawdź dane przy pomocy `SELECT`, aby upewnić się, że modyfikujesz właściwe rekordy.

> 🧪 **Uwaga:** Jeśli Twoje zapytanie `SELECT` nie zwraca wyników, dodaj kilka własnych rekordów testowych do tabeli, aby móc zrealizować zadanie.

---

## 🔹 Zadanie 1 – Aktualizacja kraju klienta

**Cel:** Zaktualizować kraj klienta na podstawie jego nazwiska.

### ✅ Zadania do wykonania:
1. Za pomocą `SELECT` znajdź klientów o nazwisku `'Smith'`.
2. Zmień ich kraj (`Country`) na `'United Kingdom'` przy pomocy `UPDATE`.
3. Sprawdź poprawność zmian przy pomocy ponownego `SELECT`.

---

## 🔹 Zadanie 2 – Zmiana MediaType utworów rockowych

**Cel:** Zmodyfikować typ nośnika (`MediaTypeId`) dla utworów z gatunku `Rock`.

### ✅ Zadania do wykonania:
1. Przygotuj `SELECT`, który pobiera wszystkie utwory z gatunku `'Rock'` oraz ich aktualny `MediaTypeId` (wymaga `JOIN` z tabelą `Genre`).
2. Zmień `MediaTypeId` tych utworów na `2` (lub inny, zależnie od dostępnych danych).
3. Wyświetl zaktualizowane dane, aby potwierdzić zmianę.

---

## 🔸 Zadanie 3 – Promocja klientów z wysokimi wydatkami

**Cel:** Wyróżnić klientów jako VIP-ów, jeśli wydali więcej niż 150 USD.

### ✅ Zadania do wykonania:
1. Dodaj kolumnę `IsVIP` typu `BOOLEAN` do tabeli `Customer` (jeśli jeszcze jej nie ma).
2. Przy pomocy `SELECT` z `JOIN` i `GROUP BY` znajdź `CustomerId` tych klientów, których wydatki przekroczyły 150 USD.
3. Zaktualizuj pole `IsVIP = TRUE` dla tych klientów.
4. Wyświetl listę klientów VIP (czyli tych, u których `IsVIP = TRUE`).

---

> 💡 **Wskazówka:** W każdej z operacji `UPDATE` warto najpierw przetestować zapytanie `SELECT`, aby upewnić się, że dane są odpowiednie. W razie potrzeby możesz też użyć `WHERE ... IN (SELECT ...)`, `JOIN`, albo `EXISTS`, w zależności od sytuacji.

# Zadania laboratoryjne – DELETE + SELECT w bazie Chinook

W poniższych zadaniach wykorzystasz `DELETE` w połączeniu z `SELECT`, aby usuwać dane z istniejących tabel. Pamiętaj, że operacja usuwania jest nieodwracalna — zawsze sprawdzaj dane przed wykonaniem polecenia `DELETE`.

> 🧪 **Uwaga:** Jeśli zapytanie `SELECT` nie zwraca żadnych wyników, dodaj dane testowe przy pomocy `INSERT`, zanim przystąpisz do usuwania.

---

## 🔹 Zadanie 1 – Usunięcie klientów z konkretnego kraju

**Cel:** Usunąć klientów z kraju, który nie jest już obsługiwany.

### ✅ Zadania do wykonania:
1. Za pomocą `SELECT` znajdź wszystkich klientów z kraju `'Argentina'`.
2. Jeśli tacy istnieją, usuń ich z tabeli `Customer` za pomocą `DELETE`.
3. Potwierdź, że rekordy zostały usunięte poprzez ponowne wykonanie `SELECT`.

---

## 🔸 Zadanie 2 – Usunięcie faktur o niskiej wartości

**Cel:** Usunąć faktury, których kwota całkowita była bardzo niska.

### ✅ Zadania do wykonania:
1. Przygotuj zapytanie `SELECT`, które znajduje wszystkie faktury (`Invoice`), których `Total` jest mniejsze niż `1.00`.
2. Usuń te rekordy z tabeli `Invoice`.
3. Upewnij się, że rekordy zostały usunięte poprzez ponowne zapytanie `SELECT` z tym samym warunkiem.

---

> 💡 **Wskazówka:** Przed każdym `DELETE` uruchom odpowiadające zapytanie `SELECT`, aby upewnić się, że usuniesz właściwe dane. Jeśli nie znajdujesz żadnych danych — dodaj je ręcznie przed kontynuowaniem.


# Zadania laboratoryjne – CREATE VIEW + SELECT w bazie Chinook

W tych zadaniach wykorzystasz polecenie `CREATE VIEW` do tworzenia widoków, które następnie zostaną wykorzystane w zwykłych zapytaniach `SELECT`. Widoki ułatwiają wielokrotne wykorzystywanie złożonych zapytań i poprawiają czytelność kodu SQL.

> 🧪 **Uwaga:** Jeśli widok opiera się na danych, które nie istnieją (np. brakujących rekordach), możesz wcześniej dodać własne dane testowe przy pomocy `INSERT`.

---

## 🔹 Zadanie 1 – Widok podstawowych danych klientów

**Cel:** Stworzyć widok z uproszczonym zestawem danych klientów.

### ✅ Zadania do wykonania:
1. Utwórz widok `BasicCustomerInfo`, który zawiera kolumny: `CustomerId`, `FirstName`, `LastName`, `Country`, `Email` z tabeli `Customer`.
2. Wykonaj zapytanie `SELECT * FROM BasicCustomerInfo`, aby wyświetlić dane.

---

## 🔹 Zadanie 2 – Widok statystyk zakupów klientów

**Cel:** Stworzyć widok podsumowujący łączną wartość zakupów każdego klienta.

### ✅ Zadania do wykonania:
1. Utwórz widok `CustomerPurchaseStats`, który zawiera:
   - `CustomerId`
   - `FullName` (połącz `FirstName` i `LastName`)
   - `TotalSpent` (suma kolumny `Total` z tabeli `Invoice`)
2. W widoku skorzystaj z `GROUP BY` i `JOIN` na tabelach `Customer` i `Invoice`.
3. Wykonaj zapytanie `SELECT * FROM CustomerPurchaseStats WHERE TotalSpent > 100`.

---

## 🔸 Zadanie 3 – Widok szczegółów zakupów według utworów 

**Cel:** Utworzyć złożony widok łączący dane o zakupach, utworach i klientach.

### ✅ Zadania do wykonania:
1. Utwórz widok `DetailedTrackSales`, który zawiera:
   - `InvoiceId`
   - `InvoiceDate`
   - `CustomerName`
   - `TrackName`
   - `ArtistName`
   - `GenreName`
   - `UnitPrice`
   - `Quantity`

   Dane pochodzą z tabel: `Invoice`, `Customer`, `InvoiceLine`, `Track`, `Album`, `Artist`, `Genre`.

2. W widoku wykorzystaj odpowiednie `JOIN`y.
3. Wykonaj zapytanie `SELECT * FROM DetailedTrackSales WHERE GenreName = 'Jazz' ORDER BY InvoiceDate DESC`.

---

> 💡 **Wskazówka:** Widoki nie przechowują fizycznie danych – są to zapisane zapytania. Po ich utworzeniu możesz traktować je jak zwykłe tabele podczas wykonywania zapytań `SELECT`.



