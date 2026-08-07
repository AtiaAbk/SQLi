# Rust — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```rust
// DO NOT DO THIS
let query = format!("SELECT * FROM users WHERE username = '{}'", username);
let rows = client.query(&query, &[]).await?;
```

## ✅ Secure: sqlx with Compile-Time-Checked Queries (Postgres)
```rust
let user = sqlx::query_as::<_, User>(
    "SELECT id, username, email FROM users WHERE username = $1"
)
.bind(&username)
.fetch_optional(&pool)
.await?;
```

## ✅ Secure: tokio-postgres with Parameters
```rust
let row = client
    .query_one(
        "SELECT id, username, email FROM users WHERE username = $1",
        &[&username],
    )
    .await?;
```

## ✅ Secure: Diesel ORM
```rust
use diesel::prelude::*;

let user = users::table
    .filter(users::username.eq(&username))
    .first::<User>(&mut conn)?;
```

## Input Validation
```rust
use regex::Regex;

fn is_valid_username(username: &str) -> bool {
    let re = Regex::new(r"^[a-zA-Z0-9_]{3,32}$").unwrap();
    re.is_match(username)
}
```

> Rust's strong typing and crates like `sqlx` (which validate queries against your schema at compile time) make certain classes of SQLi mistakes structurally harder — but parameterization is still the actual defense, not the type system alone.
