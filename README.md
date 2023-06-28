<!-- hide -->
# Connecting to a SQL Database Project Tutorial
<!-- endhide -->

- Create a SQL database localy using the psql command.
- Understand and get used to the most basic profesional python project structure with PIP and `.env` file.
- Use SQLAlchemy the most popular library in the industry for connecting to SQL databases.
- Use Pandas to display SQL Tables as dataframes.

Inside this repository, you will find a file called `./INSTRUCTIONS.md` with the steps needed to complete it.

## 🌱 How to start this project

This project comes with the necessary files to start working immediately.

We recommend opening this very same repository using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can clone it on your local computer using the `git clone` command. 

This is the repository you need to fork and open:

```
https://github.com/4GeeksAcademy/connecting-to-a-sql-database-project-tutorial
```

**👉 Please follow these steps on** [how to start a coding project](https://4geeks.com/lesson/how-to-start-a-project).

Once Gitpod VSCode has finished opening you can go ahead and open the `problems.ipynb` file and start solving each exercise inside the notebook.

## 🚛 How to deliver this project

Once you are finished solving the exercises make sure to make your changes, then push to your repository fork and go to 4Geeks.com to upload the repository link.

# Solutions

We also incorporated the solution samples on `./src/solution.py` that we strongly suggest you only use if you are stuck for more than 30min or if you have already finished and want to compare it with your approach.

# Postgres Commands

Make sure the PSQL command line Postgres client is installed in your environment, you can try the following command to make sure.

```
$ psql --version
```

Note: If you get an error, try [following this instructions](https://www.timescale.com/blog/how-to-install-psql-on-mac-ubuntu-debian-windows/) to install psql on your computer.

## Delete Database

Delete databases on your localhost with:
```
$ dropdb -h localhost -U <username> <db_name>
```

## Create a Database

Create databases on your localhost with:
```
$ createdb -h localhost -U <username> <db_name>
```

## Manipulate data by connecting to the database

Connect to the Posgres command line client:
```
$ psql -h localhost -U <username> <db_name>
```

