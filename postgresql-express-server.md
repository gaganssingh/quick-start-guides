## PostgteSQL - Express server setup

1. Create a node project and install:

   ```
   npm i express dedent node-pg-migrate pg pg-format
   npm i -D jest nodemon supertest
   ```

2. Add scripts in `package.json`:

   ```
   "migrate": "node-pg-migrate",
   "start": "nodemon index.js"
   ```

3. Create all of the migration files (table schemas) in `migrations/xxxx.js` using:
   ```
   npm run migrate create add users table
   ```
4. Create a new db in the postgresql instance.
5. Run the OS-appropriate migration command to perform the migrations (creating all tables). E.g. for bash/zsh:
   ```
   DATABASE_URL=postgres://postgres:postgres@localhost:5432/socialnetwork npm run migrate up
   ```
6. Add seed data to the database, wither using `pg admin` or by `running a seed script` in the terminal

#### Connecting to PostgreSQL using pg:

1. Create the pool config file: `src/pool.js`
2. Connect to the pool instance and start the server inside the entrypoint file (index.js, server.js etc.)

#### Configuring PostgreSQL for testing:

1. Create a test database using `pg admin` and name it `socialnetwork-test`
2. Execute all migrations to create tables in the test db
   ```
   DATABASE_URL=postgres://postgres:postgres@localhost:5432/socialnetwork-test npm run migrate up
   ```
3. Two ways to approach making requests to the test db:
   - Create a new schema: `CREATE SCHEMA test;`. Then create a table inside the test schems:
     ```
     CREATE TABLE test.users (
        id SERIAL PRIMARY KEY,
        username VARCHAR
     );
     INSERT INTO test.users (username)
      VALUES
         ('alex'),
         ('tony');
     ```
   - Run 1 test -> Empty out the db -> Make another test -> Empty out the db -> and so forth..

#### [COMMANDS] Running migrations:

- MacOS with Postgres.app
  `DATABASE_URL=postgres://USERNAME@localhost:5432/socialnetwork npm run migrate up`

- Windows with Git Bash
  `DATABASE_URL=postgres://USERNAME:PASSWORD@localhost:5432/socialnetwork npm run migrate up`

- Windows with CMD
  `set DATABASE_URL=postgres://USERNAME:PASSWORD@localhost:5432/socialnetwork&&npm run migrate up`

- Windows with Powershell
  `$env:DATABASE_URL="postgres://USERNAME:PASSWORD@localhost:5432/socialnetwork" ; npm run migrate up`
