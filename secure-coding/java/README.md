# Java — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```java
String query = "SELECT * FROM users WHERE username = '" + username + "'";
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery(query); // untrusted input concatenated into SQL
```

## ✅ Secure: JDBC PreparedStatement
```java
String sql = "SELECT id, username, email FROM users WHERE username = ?";
try (PreparedStatement stmt = conn.prepareStatement(sql)) {
    stmt.setString(1, username);
    try (ResultSet rs = stmt.executeQuery()) {
        if (rs.next()) {
            // process result
        }
    }
}
```

## ✅ Secure: Spring Data JPA
```java
public interface UserRepository extends JpaRepository<User, Long> {
    Optional<User> findByUsername(String username); // parameterized under the hood
}
```

## ✅ Secure: Hibernate with named parameters
```java
Query<User> query = session.createQuery(
    "FROM User WHERE username = :username", User.class);
query.setParameter("username", username);
User user = query.uniqueResult();
```

## Least Privilege — Example DataSource Config
```properties
# Application account should never be the DB admin account
spring.datasource.username=app_service_user
spring.datasource.password=${DB_PASSWORD}   # injected via secrets manager / env var
```

## Input Validation
```java
private static final Pattern USERNAME_PATTERN = Pattern.compile("^[a-zA-Z0-9_]{3,32}$");

public boolean isValidUsername(String username) {
    return USERNAME_PATTERN.matcher(username).matches();
}
```
