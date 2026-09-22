# Seeding & Migrations in TypeORM Reflection

**What is the purpose of database migrations in TypeORM?**
Database migrations act as version control for your database schema. Instead of manually executing SQL queries to create tables or add columns, TypeORM generates timestamped migration files containing the exact SQL required to update the database state. This ensures that schema changes are safe, trackable, and reproducible across different environments.

**How do migrations differ from seeding?**
Migrations are strictly focused on defining and modifying the database **structure** (schema), such as creating tables, adding columns, or setting up foreign keys. Seeding, on the other hand, is the process of populating that structure with initial **data**, such as creating default admin users, role configurations, or mock data for testing environments.

**Why is it important to version-control database schema changes?**
Version-controlling the database schema guarantees consistency across the entire development team and deployment pipeline. If a new developer clones the repository, they can run the migrations to instantly perfectly replicate the production database structure. It also prevents destructive conflicts and data loss when multiple developers are modifying the database simultaneously.

**How can you roll back a migration if an issue occurs?**
If a migration introduces a bug or breaks the application, TypeORM provides an automated way to undo it. You can execute the `typeorm migration:revert` command. This triggers the `down()` method inside the most recently applied migration file, reversing the schema changes (e.g., dropping a newly created column) and restoring the database to its previous stable state.