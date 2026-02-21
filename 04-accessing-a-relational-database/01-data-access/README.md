# Step 1: Get a Database Handle and Connect

In this step, you’ll write Go code that gives you access to a MySQL database using a database handle.

## Prerequisites
- MySQL database running (e.g., via Docker).
- Database `recordings` and table `album` created using `create-tables.sql`.

## Instructions

### 1. Initialize the module
```bash
go mod init data-access
go get github.com/go-sql-driver/mysql
```

### 2. Connect to the database
Create `main.go` with the following connection logic:

```go
package main

import (
    "database/sql"
    "fmt"
    "log"
    "os"
    "github.com/go-sql-driver/mysql"
)

var db *sql.DB

func main() {
    // Capture connection properties
    cfg := mysql.NewConfig()
    cfg.User = os.Getenv("DBUSER")
    cfg.Passwd = os.Getenv("DBPASS")
    cfg.Net = "tcp"
    cfg.Addr = "127.0.0.1:3306"
    cfg.DBName = "recordings"

    // Get a database handle
    var err error
    db, err = sql.Open("mysql", cfg.FormatDSN())
    if err != nil {
        log.Fatal(err)
    }

    // Ping the database to verify the connection
    pingErr := db.Ping()
    if pingErr != nil {
        log.Fatal(pingErr)
    }
    fmt.Println("Connected!")
}
```

## Key Concepts
- **sql.DB**: This is the database handle. It’s a pool of connections, not a single connection.
- **mysql.Config**: A cleaner way to build a Data Source Name (DSN) than string concatenation.
- **db.Ping()**: Confirms that the connection parameters are correct and the server is reachable.
