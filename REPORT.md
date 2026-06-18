# Raport z testów API: Conduit Application

## Cel testów
Celem projektu było przetestowanie poprawności działania punktów końcowych API aplikacji Conduit (zgodnie z dokumentacją: https://conduit.mate.academy/api/). 

## Zakres testów
Wszystkie zapytania w kolekcji Postman są **niezależne**, co oznacza, że każde z nich zawiera własne skrypty `Pre-request` przygotowujące dane testowe. Kolekcja obejmuje:
* Rejestrację i logowanie
* Zarządzanie artykułami
* Operacje na profilach użytkowników
* Komentowanie artykułów

## Wykryte błędy (Bug Reports)

### [BUG-001] Walidacja nazwy użytkownika w endpointcie Sign-up
* **Opis:** Endpoint `POST /api/users` akceptuje nazwę użytkownika (username) przekraczającą 41 znaków, co nie powinno mieć miejsca zgodnie z założeniami biznesowymi.
* **Priorytet:** Medium
* **Status:** Zgłoszono do Jira
* **Kroki do odtworzenia:**
    1. Wyślij żądanie `POST /api/users` z obiektem `user`.
    2. W polu `username` wklej ciąg znaków dłuższy niż 41.
     3. API zwraca kod 200 OK zamiast oczekiwanego błędu walidacji.
* **Oczekiwany rezultat:** Błąd walidacji (422 Unprocessable Entity).
* **Aktualny rezultat:** Użytkownik został utworzony z błędnym formatem nazwy.

---
*Raport wygenerowany przez: [Twoje Imię i Nazwisko]*
