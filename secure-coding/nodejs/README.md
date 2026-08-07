# Node.js — Secure Data Access Examples

## ❌ Vulnerable Pattern (for recognition only)
```javascript
// DO NOT DO THIS
const query = `SELECT * FROM users WHERE username = '${username}'`;
connection.query(query, (err, results) => { /* ... */ });
```

## ✅ Secure: mysql2 with placeholders
```javascript
const [rows] = await pool.execute(
  'SELECT id, username, email FROM users WHERE username = ?',
  [username]
);
```

## ✅ Secure: node-postgres (pg) with numbered placeholders
```javascript
const result = await pool.query(
  'SELECT id, username, email FROM users WHERE username = $1',
  [username]
);
```

## ✅ Secure: Prisma ORM
```javascript
const user = await prisma.user.findUnique({
  where: { username },
});
```

## ✅ Secure: Sequelize ORM
```javascript
const user = await User.findOne({ where: { username } });
```

## Input Validation
```javascript
function isValidUsername(username) {
  return /^[a-zA-Z0-9_]{3,32}$/.test(username);
}
```

## Secrets Management
```javascript
// Never hardcode credentials — load from environment/secrets manager
const pool = new Pool({
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  host: process.env.DB_HOST,
  database: process.env.DB_NAME,
});
```
