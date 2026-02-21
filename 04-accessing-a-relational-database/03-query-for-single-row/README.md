# Step 3: Query for a Single Row

For SQL statements guaranteed to return at most one row (like searching by Primary Key), Go provides the `QueryRow` method.

## Instructions

### 1. Use QueryRow
Implement the `albumByID` function:

```go
func albumByID(id int64) (Album, error) {
    var alb Album

    row := db.QueryRow("SELECT * FROM album WHERE id = ?", id)
    if err := row.Scan(&alb.ID, &alb.Title, &alb.Artist, &alb.Price); err != nil {
        if err == sql.ErrNoRows {
            return alb, fmt.Errorf("albumsById %d: no such album", id)
        }
        return alb, fmt.Errorf("albumsById %d: %v", id, err)
    }
    return alb, nil
}
```

### 2. Call the function in main
```go
alb, err := albumByID(2)
if err != nil {
    log.Fatal(err)
}
fmt.Printf("Album found: %v\n", alb)
```

## Key Concepts
- **db.QueryRow**: Simplified version of `Query` for single results. It doesn't return an error directly; instead, errors are returned by the subsequent `Scan` call.
- **sql.ErrNoRows**: A special error value used when a query returns zero rows.
