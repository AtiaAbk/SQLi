# Python — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only — do not use)
```python
# DO NOT DO THIS: string formatting builds untrusted input into SQL text
query = f"SELECT * FROM users WHERE username = '{username}'"
cursor.execute(query)
```

## ✅ Secure: Parameterized Query (sqlite3 / psycopg2 style)
```python
import sqlite3

def get_user(conn: sqlite3.Connection, username: str):
    cursor = conn.cursor()
    # Placeholders are substituted safely by the driver, never by string building
    cursor.execute("SELECT id, username, email FROM users WHERE username = ?", (username,))
    return cursor.fetchone()
```

## ✅ Secure: psycopg2 (PostgreSQL)
```python
import psycopg2

def get_user(conn, username: str):
    with conn.cursor() as cur:
        cur.execute("SELECT id, username, email FROM users WHERE username = %s", (username,))
        return cur.fetchone()
```

## ✅ Secure: SQLAlchemy ORM
```python
from sqlalchemy import select
from models import User

def get_user(session, username: str):
    stmt = select(User).where(User.username == username)
    return session.execute(stmt).scalar_one_or_none()
```

## ✅ Secure: SQLAlchemy Core with bound parameters (when raw SQL is unavoidable)
```python
from sqlalchemy import text

def get_user(engine, username: str):
    with engine.connect() as conn:
        result = conn.execute(
            text("SELECT id, username FROM users WHERE username = :username"),
            {"username": username},
        )
        return result.fetchone()
```

## Input Validation as Defense in Depth
```python
import re

def validate_username(username: str) -> bool:
    return bool(re.fullmatch(r"[a-zA-Z0-9_]{3,32}", username))
```

## Least-Privilege Connection Example
```python
# Use a service-specific, read-only account for read-only endpoints
conn = psycopg2.connect(
    dbname="app_db",
    user="app_readonly",   # not "postgres" or a superuser role
    password=get_secret("DB_PASSWORD"),  # from a secrets manager, never hardcoded
    host="db.internal",
)
```
