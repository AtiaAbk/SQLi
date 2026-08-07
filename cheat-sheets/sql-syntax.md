# 📑 SQL Syntax Cheat Sheet

## Basic Queries
```sql
SELECT column1, column2 FROM table_name WHERE condition;
INSERT INTO table_name (col1, col2) VALUES (val1, val2);
UPDATE table_name SET col1 = val1 WHERE condition;
DELETE FROM table_name WHERE condition;
```

## Joins
```sql
SELECT a.*, b.* FROM table_a a
INNER JOIN table_b b ON a.id = b.a_id;

SELECT a.*, b.* FROM table_a a
LEFT JOIN table_b b ON a.id = b.a_id;
```

## Filtering & Aggregation
```sql
SELECT department, COUNT(*) FROM employees
GROUP BY department
HAVING COUNT(*) > 5
ORDER BY department ASC;
```

## Common Data Types (vary by engine)
| Type | MySQL | PostgreSQL | SQLite |
|---|---|---|---|
| Integer | `INT` | `INTEGER` | `INTEGER` |
| Text | `VARCHAR(n)` | `VARCHAR(n)` / `TEXT` | `TEXT` |
| Date/Time | `DATETIME` | `TIMESTAMP` | `TEXT`/`INTEGER` |
| Boolean | `TINYINT(1)` | `BOOLEAN` | `INTEGER` |

## Placeholders for Parameterized Queries (by driver)
| Language / Driver | Placeholder Style |
|---|---|
| Python (`sqlite3`, `psycopg2`) | `?` or `%s` |
| Java (JDBC `PreparedStatement`) | `?` |
| PHP (PDO) | `:name` or `?` |
| Node.js (`pg`) | `$1, $2, ...` |
| Node.js (`mysql2`) | `?` |
| C# (ADO.NET) | `@paramName` |
| Go (`database/sql`) | `?` (MySQL) / `$1` (Postgres) |
| Rust (`sqlx`) | `$1` (Postgres) / `?` (MySQL/SQLite) |

> **Rule of thumb:** if you're building a query string with `+`, string interpolation, or `.format()` using untrusted input — stop, and use a parameterized query instead. See [`secure-coding/`](../secure-coding/) for full examples.
