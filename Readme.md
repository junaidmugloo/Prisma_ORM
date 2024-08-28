## Here is a list of the commonly used Prisma commands and what they do:

1. prisma init
Initializes Prisma in your project by creating a prisma folder with a schema.prisma file and a .env file.
Example:
bash
Copy code
npx prisma init
2. prisma generate
Generates the Prisma Client based on your Prisma schema. Run this after modifying your schema.prisma.
Example:
bash
Copy code
npx prisma generate
3. prisma db push
Pushes the schema changes in your schema.prisma to your database without creating a migration. It synchronizes the Prisma schema with the database schema.
Example:
bash
Copy code
npx prisma db push
4. prisma migrate dev
Creates a new migration based on the changes in your Prisma schema and applies it to your development database.
Example:
bash
Copy code
npx prisma migrate dev --name <migration_name>
5. prisma migrate deploy
Applies all pending migrations to your production database. Use this when deploying to production.
Example:
bash
Copy code
npx prisma migrate deploy
6. prisma migrate resolve
Marks a specific migration as applied or rolled back without running it. This can be useful in scenarios where a migration was manually applied or reverted.
Example:
bash
Copy code
npx prisma migrate resolve --applied <migration_id>
7. prisma migrate reset
Resets the database by dropping all data and applying all migrations from scratch. Useful during development to start with a clean database.
Example:
bash
Copy code
npx prisma migrate reset
8. prisma db seed
Runs the seed script defined in your prisma/schema.prisma. This command helps seed your database with initial data.
Example:
bash
Copy code
npx prisma db seed
9. prisma db pull
Introspects your database schema and updates the Prisma schema file (schema.prisma) to reflect any changes in your database.
Example:
bash
Copy code
npx prisma db pull
10. prisma studio
Launches Prisma Studio, a web interface for browsing and editing your database data.
Example:
bash
Copy code
npx prisma studio
11. prisma format
Formats the Prisma schema file to a standardized format.
Example:
bash
Copy code
npx prisma format
12. prisma version
Outputs the current version of Prisma that you have installed.
Example:
bash
Copy code
npx prisma version
13. prisma validate
Validates the Prisma schema for any errors without applying any changes.
Example:
bash
Copy code
npx prisma validate
14. prisma migrate diff
Compares two database states or schema files and outputs a list of differences.
Example:
bash
Copy code
npx prisma migrate diff --from-url <DATABASE_URL_1> --to-url <DATABASE_URL_2>











## make it beautiful md # Enabling MongoDB Replica Set Locally

### Step 1: Modify MongoDB Config File

To enable replication, you need to change the replication settings in your MongoDB configuration file (mongod.conf or equivalent).

Add the following lines:

conf
replication:
  replSetName: "myReplicaSet"
### Step 2: Restart MongoDB
After making the changes, restart your MongoDB instance for the new replication settings to take effect.

### Step 3: Initiate Replica Set in Mongo Shell
Open your Mongo shell.

Switch to your desired database (for example, from test to prisma):

bash
Copy code
test> use prisma
switched to db prisma
Initiate the replica set by running the following command:

bash
Copy code
prisma> rs.initiate({
  _id: "myReplicaSet",
  members: [{ _id: 0, host: "127.0.0.1:27017" }]
})
Step 4: Verify Replica Set Status
Check that the replica set has been initiated correctly. You should see:

bash
Copy code
{ ok: 1 }


for mor info https://www.prisma.io/docs
