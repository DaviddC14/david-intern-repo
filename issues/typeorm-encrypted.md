# Using typeorm-encrypted for Data Encryption Reflection

**Why does Focus Bear double encrypt sensitive data instead of relying on database encryption alone?**
Database encryption at rest only protects the data if the physical hard drives are stolen. However, if an attacker compromises the running database or steals a database dump, the data is fully readable. Field-level encryption (double encryption) ensures that even if the database is breached, the attacker cannot read the sensitive fields without also compromising the backend application's secret encryption keys.

**How does `typeorm-encrypted` integrate with TypeORM entities?**
It integrates seamlessly using TypeORM's `transformer` property inside the `@Column()` decorator. The `EncryptionTransformer` automatically intercepts the data, encrypting it right before an `INSERT` or `UPDATE` query, and decrypting it right after a `SELECT` query, allowing the application to work with plain text while the database only sees cipher text.

**What are the best practices for securely managing encryption keys?**
Encryption keys must never be hardcoded into the source code or committed to version control. They should be stored in secure environment variables (`.env` files added to `.gitignore`), and ideally managed in production using a secure secret management service like AWS Secrets Manager or HashiCorp Vault.

**What are the trade-offs between encrypting at the database level vs. the application level?**
Database-level encryption is easier to set up and allows for normal database querying, but is less secure against active database breaches. Application-level encryption provides maximum security, but it adds processing overhead to the backend server and makes it nearly impossible to perform database-side operations like sorting (`ORDER BY`) or partial string matching (`LIKE`) on the encrypted columns.