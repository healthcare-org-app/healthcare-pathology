# pathology-service

pathology-service — domain: lab

- **Port:** 8404
- **Language:** Python 3.11 + Flask
- **Database:** `lab` (Postgres, table `pathology`)
- **Event bus:** Kafka

## API

| Method    | Path                       |
|-----------|----------------------------|
| GET       | `/api/pathology/`          |
| POST      | `/api/pathology/`          |
| GET       | `/api/pathology/<id>`      |
| PUT/PATCH | `/api/pathology/<id>`      |
| DELETE    | `/api/pathology/<id>`      |
| GET       | `/health`                  |
| GET       | `/ready`                   |

## Events

**Publishes:** (none)
**Subscribes:** (none)

## HTTP peer dependencies

- `specimen-tracking-service`
- `patients-service`
- `audit-log-service`

## Local dev

```bash
pip install -e ../../libs/py-healthcare-common
pip install -r requirements.txt
cp .env.example .env
(cd ../../infra && docker compose up -d postgres kafka kafka-init)
python -m app.main
```

## Tests

```bash
pytest
```
