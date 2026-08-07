# PHP — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```php
// DO NOT DO THIS
$query = "SELECT * FROM users WHERE username = '" . $_GET['username'] . "'";
$result = mysqli_query($conn, $query);
```

## ✅ Secure: PDO Prepared Statements
```php
$stmt = $pdo->prepare("SELECT id, username, email FROM users WHERE username = :username");
$stmt->execute(['username' => $username]);
$user = $stmt->fetch(PDO::FETCH_ASSOC);
```

## ✅ Secure: mysqli Prepared Statements
```php
$stmt = $mysqli->prepare("SELECT id, username, email FROM users WHERE username = ?");
$stmt->bind_param("s", $username);
$stmt->execute();
$result = $stmt->get_result()->fetch_assoc();
```

## ✅ Secure: Laravel Eloquent / Query Builder
```php
// Eloquent (parameterized under the hood)
$user = User::where('username', $username)->first();

// Query Builder with raw expression + bindings (safe pattern for edge cases)
$users = DB::select('SELECT * FROM users WHERE username = ?', [$username]);
```

## Configuring PDO Safely
```php
$pdo = new PDO($dsn, $user, $pass, [
    PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
    PDO::ATTR_EMULATE_PREPARES => false, // ensures true server-side prepared statements
]);
```

## Input Validation
```php
function isValidUsername(string $username): bool {
    return (bool) preg_match('/^[a-zA-Z0-9_]{3,32}$/', $username);
}
```
