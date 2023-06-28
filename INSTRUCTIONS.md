# Connecting to a SQL database from Python

## Part 1: Creating a database locally

Make sure the PSQL command line Postgres client is installed in your environment, you can try the following command to make sure.

```
$ psql --version
```

Note: If you get an error, try [following this instructions](https://www.timescale.com/blog/how-to-install-psql-on-mac-ubuntu-debian-windows/) to install psql on your computer.


1. Create a Database with `createdb -h localhost -U <username> <db_name>`.
2. Connect to the Posgres command line client with `$ psql -h localhost -U <username> <db_name>`

You are able to run any SQL command inside your recently created database, you can do queries, create tables, delete tables, etc.


## Part 2: Understand your project template structure

Your SQL database has been created, but there are no tables yet. You are going to connect to your empty database and create some tables from Python using SQL Scripts we have alreadly provided for you inside the `./src/sql/` folder:

- `./src/sql/create.sql` with all the tables you need to create. Hands on creating those tables.
- `./src/sql/insert.sql` with all the table values to be inserted into each table.
- `./src/sql/drop.sql` contains the SQL code to delete the tables, very useful to clean your database.

Other important things to mention about the structure:

- Professional projects usually have a `./src` folder that contains all the "coding files" (the files that the developer will code).
- The `./assets` is irrelevant to you, it contains all the images we needed for this tutorial.
- The `root` of any professional project usally contains all the configuration files like `.gitignore`, `requirements.txt`, etc. You will learn more about these files during the rest of the project.

### Part 3: Install dependencies

There is a file in this project called `./requirements.txt` that contains the list of python libraries we will be using in this project like Pandas, psycopg2, SQLAlchemy, etc. Run the `pip install -r requirements.txt` command to install all the libraries at once.

This is possible thanks to PIP (the most popular Python package manager) and how professionals install their project dependencies.

> NOTE: Make sure the command does not output any errors in the terminal.

### Part 4: Add your database credentials 

Create your .env file: It is a good practice that every python application must have a `.env` file, the file name starts with a `.` dot because its a configuration file that will be ignored by your Git repository. It needs to be ignored because we are going to be adding our database password inside that file. 

Type your database credentials inside the `.env` file, the file will end up looking like this:

```
DB_USER = 'hkietatgd83b4x0l'
DB_PASSWORD = 'p0s2wasdado1cr02d12'
DB_PORT = 3306
DB_HOST = 'f565gmi022AD.cbetxkdyhwsb.us-east-1.rds.amazonaws.com'
DB_NAME = 'y9uflxvx2hsf11g3f'
```

Note: Please make sure to replace this values with your real database credentials.

### Part 5: Start coding

All your Python code must always be inside the `src` folder, this is also another good practice.

1. The `connect` function contains the necesary code to connect to your python database, if you watch carefully you will see how it loads all the environment variables into a `connection_string` variable and then it calls the `create_engine` and `connect` fuctions.

```py
def connect():
    global engine # this allows us to use a global variable called engine
    # A "connection string" is basically a string that contains all the databse credentials together
    connection_string = f"postgresql://{os.getenv('DB_USER')}:{os.getenv('DB_PASSWORD')}@{os.getenv('DB_HOST')}/{os.getenv('DB_NAME')}?autocommit=true"
    print("Starting the connection...")
    engine = create_engine(connection_string)
    engine.connect()
    return engine
```

## 📝 Instructions:

1. Let's create a file inside the `src` folder called `./src/app.py`.

> Note: This file will contain most of your application code; The database conection and the database queries.

2. Create a cloud database using Heroku as indicated in part 1.

3. In your app.py connect to your database

4. Create the tables indicated in `./src/sql/create.sql`

5. Insert the data indicated in `./src/sql/insert.sql` to your recently created tables.

6. Use pandas to print one of the tables as dataframes using read_sql function


## Aditional tips

- To login inside postgress localy you can run: `psql -h localhost -u postgres`
- Connect to a remote database: `psql -h <REMOTE HOST> -p <REMOTE PORT> -U <DB_USER> <DB_NAME>`
- Delete databases on your localhost with: `$ dropdb -h localhost -U <username> <db_name>`
- You can try creating a cloud database on render.com by [following these commands](https://render.com/docs/databases#connecting-from-outside-render).