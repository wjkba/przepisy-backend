# przepisy-backend

[![Python - 3.12](https://img.shields.io/badge/Python-3.12-3776AB)](https://www.python.org/)
[![FastAPI - 0.110.2](https://img.shields.io/badge/FastAPI-0.110.2-009688)](https://fastapi.tiangolo.com/)
[![uvicorn - 0.29.0](https://img.shields.io/badge/uvicorn-0.29.0-499848)](https://www.uvicorn.org/)


Aplikacja została zbudowana przy użyciu FastAPI, nowoczesnego, szybkiego i wysoko wydajnego frameworka webowego do budowania interfejsów API z Pythonem 3.7+ opartego na standardowych wskazówkach typów Pythona.

## Funkcje 
- Uwierzytelnianie i autoryzacja użytkowników przy użyciu JWT
- Bezpieczne hashowanie haseł
- Obsługa przesyłania plików dla obrazów przepisów
- Operacje CRUD dla przepisów
- Operacje asynchroniczne dla lepszej wydajności

## Wykorzystane technologie
- FastAPI: Główny framework webowy używany do tworzenia API.
- Uvicorn: Implementacja serwera ASGI używana do obsługi aplikacji FastAPI.
- Passlib: Biblioteka do bezpiecznego hashowania haseł.
- python-multipart: Wymagane do obsługi danych formularza (używane do przesyłania plików).
- python-jose: Implementacja JavaScript Object Signing and Encryption (JOSE) w Pythonie, używana do tworzenia i weryfikacji JWT.
- Pillow: Fork biblioteki Python Imaging Library (PIL) używanej do przetwarzania obrazów.
- aiofiles: Biblioteka do asynchronicznej obsługi operacji plikowych.
- JWT: Tokeny JSON Web dla bezpiecznego uwierzytelniania i wymiany informacji.

## Instalacja

## Konfiguracja

## Funkcjonalność
### Przepisy
- **Pobieranie przepisów**
  - `GET /api/recipes` - Pobiera listę wszystkich przepisów.
  - `GET /api/recipe/{recipe_id}` - Pobiera szczegóły przepisu o określonym identyfikatorze.
  - `GET /api/recipes/newest` - Pobiera listę najnowszych przepisów.
  - `GET /api/recipes/trending` - Pobiera listę najbardziej popularnych przepisów.
  - `GET /api/recipes/{username}` - Pobiera przepisy użytkownika o określonej nazwie użytkownika.
  - `GET /saved-recipes` - Pobiera listę zapisanych przepisów użytkownika. Wymaga uwierzytelniania.

- **Usuwanie przepisu**
  - `DELETE /api/recipe/{id}` - Usuwa przepis o określonym identyfikatorze. Wymaga uwierzytelniania.

- **Przesyłanie obrazu przepisu**
  - `POST /upload/recipe-image` - Endpoint umożliwiający przesyłanie obrazów przepisów. Obraz jest przetwarzany, przeskalowany i zapisywany na serwerze. Zwraca URL do zapisanego obrazu.

- **Tworzenie przepisu**
  - `POST /api/recipe` - Tworzy nowy przepis. Wymaga uwierzytelniania.

- **Aktualizacja przepisu**
  - `PUT /api/recipe/{id}` - Aktualizuje istniejący przepis. Wymaga uwierzytelniania.

### Użytkownicy
- **Rejestracja użytkownika**
  - `POST /api/sign_up` - Rejestruje nowego użytkownika.
 
- **Zapisywanie i usuwanie zapisanych przepisów**
  - `POST /api/save_recipe/{recipe_id}` - Zapisuje przepis o określonym identyfikatorze do listy zapisanych przepisów użytkownika. Wymaga uwierzytelniania.
  - `POST /api/unsave_recipe/{recipe_id}` - Usuwa przepis o określonym identyfikatorze z listy zapisanych przepisów użytkownika. Wymaga uwierzytelniania.
 
- **Sprawdzenie uwierzytelniania**
  - `GET /authcheck` - Endpoint sprawdzający, czy użytkownik jest zalogowany. Zwraca komunikat "please log in" dla niezalogowanych użytkowników lub "Authorized" dla zalogowanych.




