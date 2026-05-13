# Project Setup

## Start the Environment

To completely stop and remove containers, networks, and volumes:

```bash
docker compose down -v
```

To rebuild and start everything:

```bash
docker compose up --build
```

---

# Project Structure

Example structure:

```text
.
├── docker-compose.yml
├── Dockerfile
├── requirements.txt
├── notebooks/
├── data/
├── src/
└── README.md
```

---

# Purpose of Each Component

## `docker-compose.yml`

Defines and orchestrates the services used by the project.

Typical responsibilities:

- builds containers
- exposes ports
- mounts volumes
- sets environment variables
- starts services together

Example:

```yaml
services:
  jupyter:
    build: .
    ports:
      - "18890:8888"
```

This maps:

```text
host port 18890 → container port 8888
```

---

## `Dockerfile`

Defines how the container image is built.

Usually contains:

- base image
- Python installation
- dependency installation
- Jupyter configuration
- startup command

Example:

```dockerfile
FROM python:3.11

RUN pip install jupyterlab pandas matplotlib seaborn
```

---

## `requirements.txt`

Lists Python dependencies.

Example:

```text
pandas
matplotlib
seaborn
jupyterlab
psycopg2-binary
sqlalchemy
```

Used during image build:

```dockerfile
RUN pip install -r requirements.txt
```

---

## `notebooks/`

Contains Jupyter notebooks (`.ipynb` files).

Typical usage:

- data exploration
- visualisation
- experimentation
- analysis

---

## `data/`

Stores datasets used by notebooks/scripts.

Examples:

```text
data/
├── cars.csv
└── processed/
```

---

## `src/`

Contains reusable Python code.

Examples:

- utility functions
- preprocessing logic
- plotting helpers
- business logic

---

# JupyterLab Connection

After running:

```bash
docker compose up --build
```

JupyterLab becomes available at:

```text
http://127.0.0.1:18890/lab?token=<TOKEN>
```

---

# Authentication Token

The token comes from the Jupyter startup configuration in the Dockerfile.

Example:

```dockerfile
CMD ["jupyter", "lab",
     "--ip=0.0.0.0",
     "--port=8888",
     "--no-browser",
     "--allow-root",
     "--IdentityProvider.token=<TOKEN>"]
```

Example usage:

```text
http://127.0.0.1:18890/lab?token=mytoken123
```

---

# Port Mapping Explanation

18890:8888 means:

- container runs on 8888
- host accesses via 18890

---

# PostgreSQL Integration

```yaml
services:
  postgres:
    image: postgres:16
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
      POSTGRES_DB: cars_db
    ports:
      - "5432:5432"
```

---

# Query PostgreSQL via Docker

```bash
docker compose exec postgres psql -U postgres
```

---

## Specific DB

```bash
docker compose exec postgres psql -U postgres -d cars_db
```

---

## Useful commands

\l  list DBs  
\dt list tables  
\d table  
\q  quit  

---

# Python connection

```python
postgresql://postgres:postgres@postgres:5432/cars_db
```

```python
from sqlalchemy import create_engine

engine = create_engine("postgresql://postgres:postgres@postgres:5432/cars_db")
```

---

# Host connection

```bash
psql -h localhost -U postgres -d cars_db
```
