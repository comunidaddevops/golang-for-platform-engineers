# 🗄️ Phase 4: Accessing a relational database

![Gopher Coding](./../media/coding.png)

In this tutorial, you’ll learn how to access a relational database from Go. You’ll use the `database/sql` package and a MySQL driver to perform common database operations. 🐳

## Tutorial Sequence

The tutorial is divided into four main sections:

1.  **[Get a database handle and connect](./01-data-access/README.md)**: Set up your environment and establish a connection.
2.  **[Query for multiple rows](./02-query-for-multiple-rows/README.md)**: Execute SQL SELECT statements that return multiple rows.
3.  **[Query for a single row](./03-query-for-single-row/README.md)**: Use `QueryRow` to fetch a specific record by its ID.
4.  **[Add data](./04-add-data/README.md)**: Use `Exec` to perform INSERT operations and retrieve the new row ID.

---

## Setup Environment

To follow this tutorial, you need a MySQL database. We use Docker to spin up a container with the required settings.

1.  **Start MySQL**: Use the provided `docker-compose.yaml` file.
    ```bash
    docker-compose up -d
    ```
2.  **Initialize Tables**: Run the `create-tables.sql` script in your MySQL instance to create the `recordings` database and the `album` table.

---

> [!IMPORTANT]
> Ensure you set the environment variables `DBUSER` and `DBPASS` before running the Go programs so they can authenticate with the database.
