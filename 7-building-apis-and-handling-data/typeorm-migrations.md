## Reflection - TypeORM Migrations

### What is the purpose of database migrations in TypeORM?

Migrations are used to track and apply changes to the database schema over time. Instead of editing the database manually, we use migrations to keep it consistent and versioned.

### How do migrations differ from seeding?

Migrations change the structure of the database (like adding columns), while seeding is about adding initial or test data into the tables.

### Why is it important to version-control database schema changes?

So that everyone on the team has the same database structure. It also helps us keep track of what changed and when, and makes it easier to debug or revert if something breaks.

### How can you roll back a migration if an issue occurs?

We can run the revert command to undo the last migration:
npm run typeorm migration:revert -- -d ./data-source.ts
