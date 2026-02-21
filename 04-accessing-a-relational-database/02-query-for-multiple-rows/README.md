# Step 2: Query for Multiple Rows

In this section, you’ll use Go to execute an SQL query designed to return multiple rows from the `album` table.

## Instructions

### 1. Define the Album struct
Add a struct to represent the database row:

```go
type Album struct {
    ID     int64
    Title  string
    Artist string
    Price  float32
}
```

### 2. Implement the Query function
Use the `db.Query` method to fetch data:

```go
func albumsByArtist(name string) ([]Album, error) {
    var albums []Album

    rows, err := db.Query("SELECT * FROM album WHERE artist = ?", name)
    if err != nil {
        return nil, fmt.Errorf("albumsByArtist %q: %v", name, err)
    }
    defer rows.Close()

    // Loop through rows
    for rows.Next() {
        var alb Album
        if err := rows.Scan(&alb.ID, &alb.Title, &alb.Artist, &alb.Price); err != nil {
            return nil, fmt.Errorf("albumsByArtist %q: %v", name, err)
        }
        albums = append(albums, alb)
    }
    if err := rows.Err(); err != nil {
        return nil, fmt.Errorf("albumsByArtist %q: %v", name, err)
    }
    return albums, nil
}
```

## Key Concepts
- **db.Query**: Used for SELECT statements that return multiple rows.
- **rows.Next()**: Iterates through the result set.
- **rows.Scan**: Copies values from the current row into Go variables.
- **SQL Injection Prevention**: Using the `?` placeholder ensures the driver handles parameter escaping.
