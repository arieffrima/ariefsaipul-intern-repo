### Reflection on @nestjs/typeorm

#### How does @nestjs/typeorm simplify database interactions?
So, when I use `@nestjs/typeorm`, it makes working with databases super easy, Instead of writing complex SQL queries, I just use decorators like `@Entity()` and `@Column()` to define my tables and columns. Plus, it integrates seamlessly with NestJS, so I don’t have to worry about manually setting up database connections or doing a bunch of setup – it just works!

---

#### What is the difference between an entity and a repository in TypeORM?
- **Entity**: I think of an entity like a blueprint for a database table. It defines the structure of the data, like the columns and their types. It’s just a class with some cool decorators to map it to the database.
- **Repository**: The repository is like a helper that gives me methods to interact with the database. So, instead of writing SQL manually, I use repository methods to get data, insert, update, or delete records. It’s like a data manager for me!

---

#### How does TypeORM handle migrations in a NestJS project?
Migrations are like a way to keep my database schema in check as I update my code. With TypeORM, I can generate migrations using `typeorm migration:generate`, and then I can run them with `typeorm migration:run`. This helps me keep my database up to date without worrying about breaking things, especially when working in a team.

---

#### What are the advantages of using PostgreSQL over other databases in a NestJS app?
PostgreSQL is pretty awesome, it's reliable and ensures data integrity, which is super important. 


![Screenshot 2025-03-17 223914](https://github.com/user-attachments/assets/748dee69-a468-4866-b009-6dc77a664a88)

#### https://github.com/arieffrima/arief-nestjs/tree/feature
