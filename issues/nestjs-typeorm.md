# Connecting to PostgreSQL with TypeORM in NestJS Reflection

**How does `@nestjs/typeorm` simplify database interactions?**
The `@nestjs/typeorm` package integrates TypeORM seamlessly with NestJS's dependency injection system. It allows developers to easily register database connections globally or per-module and inject Repositories directly into Services using the `@InjectRepository()` decorator, completely abstracting away the manual instantiation of database connections.

**What is the difference between an entity and a repository in TypeORM?**
An **Entity** is a class decorated with `@Entity()` that directly maps to a database table; it defines the structure, columns, and relationships (the "schema"). A **Repository**, on the other hand, is a class provided by TypeORM that acts as the data access layer. It contains built-in methods (like `find`, `save`, `update`, and `delete`) to interact with the database records associated with a specific Entity.

**How does TypeORM handle migrations in a NestJS project?**
In a professional NestJS project, TypeORM migrations are typically handled via the TypeORM CLI rather than letting the application auto-synchronize (`synchronize: true`). Developers create a separate `data-source.ts` file for the CLI, generate SQL migration files based on changes made to the Entities, and then run these migrations against the database. This ensures strict version control over schema changes.

**What are the advantages of using PostgreSQL over other databases in a NestJS app?**
PostgreSQL is a highly robust, open-source relational database that excels in complex queries, data integrity, and strict ACID compliance. For modern NestJS apps, its major advantage is its advanced feature set, such as native support for JSONB data types (allowing NoSQL-like flexibility within a relational structure), arrays, and powerful indexing capabilities.