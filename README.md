# GitHub Actions — lekcja 1 (repo startowe)

Repozytorium przygotowane do pierwszej lekcji o GitHub Actions.

## Co już działa
- prosta aplikacja Flask,
- 2 testy w `pytest`,
- `Dockerfile`,
- `docker-compose.yml`.

## Czego jeszcze nie ma
- brak katalogu `.github/workflows/`,
- brak pipeline'u CI.

## Cel na lekcji
Dodać pierwszy workflow GitHub Actions, który:
1. uruchamia się na `push` i `pull_request`,
2. instaluje zależności,
3. uruchamia testy `pytest`.

## Uruchomienie lokalne
```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
pytest -q
python app.py
```

## Uruchomienie w Dockerze
```bash
docker build -t gha-lesson-1 .
docker run -p 8000:8000 gha-lesson-1
```

## Uruchomienie w Docker Compose

```bash
docker compose up -d
```

## Przykładowy przebieg pracy na lekcji
1. Utwórz branch `feature/first-ci`.
2. Dodaj plik `.github/workflows/ci.yml`.
3. Wypchnij branch do GitHuba.
4. Otwórz Pull Request.
5. Sprawdź wynik pipeline'u w zakładce **Checks** i **Actions**.
6. Celowo zepsuj test, zobacz czerwony pipeline, napraw i ponów.


# GitHub Actions - lekcja 2

Repo startowe do lekcji o wielu jobach w CI.

## Masz już gotowe
- prostą aplikację Flask,
- testy `pytest`,
- `Dockerfile` i `docker-compose.yml`,
- workflow z jednym jobem testowym z lekcji 1.

## Cel tej lekcji
Rozbudować workflow tak, aby miał osobny job `lint`, osobny job `test`, zależność `needs` oraz dwa czytelne statusy w Pull Requeście.

## Uruchomienie lokalne
```bash
pip install -r requirements.txt
ruff check .
pytest -q
```

## Szybki błąd demonstracyjny
Dopisz na początku `app/main.py` linię `import os`.
Ruff zgłosi wtedy nieużywany import.

