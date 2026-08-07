# Go — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```go
query := fmt.Sprintf("SELECT * FROM users WHERE username = '%s'", username)
rows, err := db.Query(query)
```

## ✅ Secure: database/sql with Placeholders
```go
row := db.QueryRow("SELECT id, username, email FROM users WHERE username = ?", username)

var id int
var uname, email string
if err := row.Scan(&id, &uname, &email); err != nil {
    // handle error
}
```

## ✅ Secure: PostgreSQL with pgx / lib/pq (numbered placeholders)
```go
row := db.QueryRow(context.Background(),
    "SELECT id, username, email FROM users WHERE username = $1", username)
```

## ✅ Secure: sqlx (still parameterized)
```go
var user User
err := db.Get(&user, "SELECT * FROM users WHERE username = ?", username)
```

## ✅ Secure: GORM
```go
var user User
result := db.Where("username = ?", username).First(&user)
```

## Input Validation
```go
import "regexp"

var usernamePattern = regexp.MustCompile(`^[a-zA-Z0-9_]{3,32}$`)

func isValidUsername(username string) bool {
    return usernamePattern.MatchString(username)
}
```
