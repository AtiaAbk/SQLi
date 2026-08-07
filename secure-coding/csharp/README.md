# C# — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```csharp
string query = "SELECT * FROM Users WHERE Username = '" + username + "'";
var command = new SqlCommand(query, connection);
```

## ✅ Secure: ADO.NET Parameterized Query
```csharp
string sql = "SELECT Id, Username, Email FROM Users WHERE Username = @Username";
using var command = new SqlCommand(sql, connection);
command.Parameters.AddWithValue("@Username", username);
using var reader = command.ExecuteReader();
```

## ✅ Secure: Entity Framework Core (LINQ)
```csharp
var user = await dbContext.Users
    .FirstOrDefaultAsync(u => u.Username == username);
```

## ✅ Secure: EF Core Raw SQL with Parameters (when raw SQL is unavoidable)
```csharp
var users = await dbContext.Users
    .FromSqlInterpolated($"SELECT * FROM Users WHERE Username = {username}")
    .ToListAsync();
// FromSqlInterpolated safely parameterizes interpolated values — never use FromSqlRaw with string concatenation
```

## Input Validation
```csharp
using System.Text.RegularExpressions;

public static bool IsValidUsername(string username) =>
    Regex.IsMatch(username, @"^[a-zA-Z0-9_]{3,32}$");
```

## Secrets Management
```csharp
// appsettings.json should never contain plaintext production credentials —
// use environment variables, Azure Key Vault, or AWS Secrets Manager instead.
var connectionString = Environment.GetEnvironmentVariable("DB_CONNECTION_STRING");
```
