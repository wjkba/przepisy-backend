# przepisy-backend

Metody i techniki programowania - Semestr letni 2023/2024

[![Python - 3.12](https://img.shields.io/badge/Python-3.12-3776AB)](https://www.python.org/)
[![FastAPI - 0.110.2](https://img.shields.io/badge/FastAPI-0.110.2-009688)](https://fastapi.tiangolo.com/)
[![uvicorn - 0.29.0](https://img.shields.io/badge/uvicorn-0.29.0-499848)](https://www.uvicorn.org/)
[![MongoDB -  ](https://img.shields.io/badge/MongoDB-_-00ed64)](https://www.mongodb.com/)


Aplikacja została zbudowana przy użyciu FastAPI, nowoczesnego, szybkiego i wysoko wydajnego frameworka webowego do budowania interfejsów API z Pythonem 3.7. API łączy się z lokalnym serwerem MongoDB działającym na porcie 27017. Baza danych MongoDB została nazwana 'szpinak_db' i zawiera dwie kolekcje: 'recipes_collection', w której przechowywane są przepisy, oraz 'users_collection', gdzie przechowywane są dane użytkowników. 

Dzięki temu backend aplikacji umożliwia komunikację między frontendem a serwerem, zapewniając pełną funkcjonalność zarządzania przepisami. Użytkownicy mogą wygodnie pobierać, dodawać, aktualizować, usuwać i zapisywać ulubione przepisy, korzystając z interakcji z aplikacją.


## Funkcje 
- Uwierzytelnianie i autoryzacja użytkowników przy użyciu JWT
- Bezpieczne hashowanie haseł
- Obsługa przesyłania plików dla obrazów przepisów
- Operacje CRUD dla przepisów
- Operacje asynchroniczne dla lepszej wydajności

## Wykorzystane biblioteki
- **FastAPI**: Główny framework webowy używany do tworzenia API.
- **Uvicorn**: Implementacja serwera ASGI używana do obsługi aplikacji FastAPI.
- **Passlib**: Biblioteka do bezpiecznego hashowania haseł.
- **python-multipart**: Wymagane do obsługi danych formularza (używane do przesyłania plików).
- **python-jose**: Implementacja JavaScript Object Signing and Encryption (JOSE) w Pythonie, używana do tworzenia i weryfikacji JWT.
- **Pillow**: Fork biblioteki Python Imaging Library (PIL) używanej do przetwarzania obrazów.
- **aiofiles**: Biblioteka do asynchronicznej obsługi operacji plikowych.
- **JWT**: Tokeny JSON Web dla bezpiecznego uwierzytelniania i wymiany informacji.

## Konfiguracja
Wymagana jest wcześniejsza instalacja programów umożliwiających działanie bazy danych MongoDB
- [MongoDB Shell](https://www.mongodb.com/try/download/shell) 
- [MongoDB Community Server](https://www.mongodb.com/try/download/community)
- [MongoDB Compass](https://www.mongodb.com/products/tools/compass)
<br/>

1. Pobierz repozytorium
2. W aplikacji MongoDB Compass stwórz nową baze danych o nazwie `szpinak_db`
3. Stwórz dwie kolekcje `recipes` i `users`
4. Zaimportuj dane z folderu `mongodb_data`
5. Przy użyciu konsoli wejdź do ścieżki `backend`, zainstaluj pipenv i wymagane zależności
```
pip install pipenv
```
```
pipenv install
```
6. Uruchom server przy użyciu uvicorn na porcie 8000
```
pipenv shell
```
```
uvicorn main:app --reload --port 8000
```

dokumentacja dostępna pod adresem http://127.0.0.1:8000/docs

## Żądania HTTP

### Użytkownicy, uwierzytelnianie

- `POST /api/sign_up` - Tworzy nowe konto użytkownika.
- `GET /api/authcheck` - Sprawdza, czy bieżący użytkownik jest uwierzytelniony.
- `GET /api/v` - Waliduje token użytkownika.
- `GET /api/verify-token/{token}` - Weryfikuje podany token.
- `POST /api/token` - Loguje użytkownika i zwraca token uwierzytelniający.

### Przepisy GET

- `GET /api/recipes` - Pobiera listę wszystkich przepisów.
- `GET /api/recipe/{recipe_id}` - Pobiera przepis na podstawie ID.
- `GET /api/recipes/newest` - Pobiera najnowsze przepisy.
  - Parametry zapytania: n - liczba najnowszych przepisów do pobrania.
- `GET /api/recipes/trending` - Pobiera najczęściej oglądane przepisy.
  - Parametry zapytania: n - liczba najczęściej oglądanych przepisów do pobrania.
- `GET /api/recipes/{username}` - Pobiera przepisy utworzone przez konkretnego użytkownika.
- `GET /api/saved-recipes` - Pobiera przepisy zapisane przez bieżącego użytkownika.

### Przepisy CUD (Create, Update, Delete)

- `POST /api/recipe` - Tworzy nowy przepis.
- `PUT /api/recipe/{id}` - Aktualizuje istniejący przepis (obecnie niezaimplementowane).
- `DELETE /api/recipe/{id}` - Usuwa przepis na podstawie ID.
- `POST /api/save_recipe/{recipe_id}` - Zapisuje przepis w zapisanych przepisach bieżącego użytkownika.
- `POST /api/unsave_recipe/{recipe_id}` - Usuwa przepis z zapisanych przepisów bieżącego użytkownika.
- `POST /api/upload/recipe-image` - Przesyła obrazek do przepisu.






