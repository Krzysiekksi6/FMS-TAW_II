# Nazwa kursu
Technologie Aplikacji Webowych II PROJEKT
# Autor
Krzysztof Książek
# Temat projektu

System zarządzania zasobami żywnościowymi oraz dietą

# Opis projektu

W ramach realizacji projektu zostanie zaprojektowana oraz
zaimplementowana aplikacja, która będzie miała na celu zarządzaniem
dietą użytkownika.


# Uruchomienie projektu

1. Uruchom komendę `npm i` w terminalu 
2. Skonfiguruj bazę danych wewnątrz pliku `src/config/connectDatabase.ts`
3. Uruchom komendę `docker compose up -d` aby uruchomić instancję bazy danych w tle
4. Uruchom komendę `npm run start` lub `npm run dev`
5. Uruchom komendę `docker compose down` aby zatrzymać działanie instancji bazy danych

# Uruchomienie testów jednostkowych i integracyjnych

1. Uruchom komendę `npm run test` aby uruchomić wszystkie testy
2. Uruchom komendę `npx jest register.test.ts` aby uruchomić pojedyncze testy

# Dodatkowe informacje dla prowadzącego

1. W katalogu głównym folderze `docs/tests` znajdują się wycinki ekranu `.png` przedstawiające uruchomienie testów jednostkowcyh oraz integracyjnych. 

# Dokumentacja API

## Rejestracja użytkownika

### Adres usługi
`/register`,

### TYP: `POST`,

### Opis
Rejestracja nowego użytkownika.


### Przyjmuje
```json
{
  "firstname": "John",
  "lastname": "Doe",
  "username": "johndoe123",
  "password": "securepassword"
}
```
### Zwraca: `201 Created || 409 Conflict`

## Autoryzacja użytkownika

### Adres usługi
`/auth`

### TYP: `POST`

### Opis
Proces autoryzacji użytkownika.

### Przyjmuje
```json
{
  "username": "johndoe123",
  "password": "securepassword"
}
```
### Zwraca: `200 OK || 400 Bad Request || 401 Unauthorized`
- 200 OK: Pomyślne zalogowanie użytkownika. Odpowiedź zawiera komunikat potwierdzający logowanie, np. "User: johndoe123 is logged in".

- 400 Bad Request: Błąd związany z niepoprawnym formatem żądania. Odpowiedź może zawierać komunikat, np. "Username and password are required".

- 401 Unauthorized: Błąd autoryzacji. Odpowiedź zawiera komunikat o braku autoryzacji, np. "Unauthorized".

## Szczegóły użytkownika

### Adres usługi
`/users/:id/details`

### TYP: `PUT`

### Opis
Aktualizuje  szczegóły użytkownika o określonym identyfikatorze.

### Parametry ścieżki
- `id` (parametr ścieżki): Identyfikator użytkownika.

### Przyjmuje
```json
{
  "age": 25,
  "weight": 70,
  "height": 175,
  "chestCircumference": 95,
  "waistCircumference": 80,
  "hipCircumference": 90,
  "armCircumference": 30,
  "thighCircumference": 50,
  "calfCircumference": 35
}
```

### Zwraca: 200 OK || 400 Bad Request || 404 Not Found

- 200 OK: Pomyślne zaktualizowanie szczegółów użytkownika. Odpowiedź zawiera zaktualizowane szczegóły użytkownika, w tym także obliczone BMI.

- 400 Bad Request: Błąd związany z niepoprawnym formatem żądania. Odpowiedź może zawierać komunikat, np. "Invalid data".

- 404 Not Found: Brak użytkownika o podanym identyfikatorze. Odpowiedź zawiera komunikat, np. "User not found".

