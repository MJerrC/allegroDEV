# Price_statement

Aplikacja pobiera najniższe ceny rynkowe zestawów LEGO z publicznych ofert Allegro i zapisuje je w bazie domowego budżetu (`budzet_dom`). Działa raz w tygodniu.

## Cel

Kafelek każdego zestawu w kolekcji LEGO pokazuje najniższą cenę rynkową na dziś. Aplikacja uzupełnia tę wartość automatycznie, zamiast ręcznego sprawdzania ofert.

## Jakie dane są pobierane

- Publiczne oferty z Allegro dla wyszukiwanych zestawów (endpoint `GET /offers/listing`).
- Z każdej oferty: tytuł, cenę i podstawowe dane potrzebne do dopasowania do zestawu.

Aplikacja nie pobiera danych osobowych, zamówień, płatności ani danych sprzedawców. Nie zmienia żadnych ofert.

## Uwierzytelnianie

- Wyszukiwanie publicznych ofert działa w oparciu o **Client ID** i **Client Secret** aplikacji (flow client credentials). Nie wymaga logowania użytkownika Allegro.
- Zakres `allegro:api:sale:offers:read` jest zaznaczony w rejestracji, ale nie jest wymagany do publicznego wyszukiwania. Zostawiony na wypadek przyszłego odczytu własnych ofert.


## Wymagania API

- Każde zapytanie musi zawierać nagłówek `User-Agent` wygenerowany w [Generatorze User-Agent](https://apps.developer.allegro.pl/) dla tej aplikacji. Bez niego klucz API może zostać zablokowany.
- Wersja aplikacji: 1.8.0.
- Limit Allegro REST API to 9000 zapytań na minutę na Client ID. Aplikacja wykonuje tylko kilkadziesiąt zapytań tygodniowo, więc limit nie jest problemem.

## Harmonogram

Aktualizacja raz w tygodniu. Wynik zapisuje do tabeli cen rynkowych w `budzet_dom`.


## Dokumentacja i kontakt

- Autor: [Maciej Chmiel]
- Kontakt: [maciejchmiel@bespokeit.pl]
- Dokumentacja Allegro: [developer.allegro.pl](https://developer.allegro.pl/about)

## Zgodność

Aplikacja jest prywatnym narzędziem do śledzenia cen własnej kolekcji. Nie udostępnia danych innym osobom ani nie służy do sprzedaży.
