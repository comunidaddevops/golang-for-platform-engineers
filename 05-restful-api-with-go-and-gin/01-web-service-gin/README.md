# Developing a RESTful API with Gin

This step covers designing and building a RESTful API to manage a collection of albums.

## API Endpoint Design

We’ll build three endpoints:

| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/albums` | `GET` | Returns all albums as JSON. |
| `/albums` | `POST` | Adds a new album from JSON body. |
| `/albums/:id` | `GET` | Returns a specific album by ID. |

## Instructions

### 1. Initialize the module
```bash
go mod init example/web-service-gin
go get github.com/gin-gonic/gin
```

### 2. Create the data structure
In `main.go`, define the `album` struct with JSON tags:

```go
type album struct {
    ID     string  `json:"id"`
    Title  string  `json:"title"`
    Artist string  `json:"artist"`
    Price  float64 `json:"price"`
}
```

### 3. Implement Handlers

#### GET All Albums
```go
func getAlbums(c *gin.Context) {
    c.IndentedJSON(http.StatusOK, albums)
}
```

#### POST a New Album
```go
func postAlbums(c *gin.Context) {
    var newAlbum album
    if err := c.BindJSON(&newAlbum); err != nil {
        return
    }
    albums = append(albums, newAlbum)
    c.IndentedJSON(http.StatusCreated, newAlbum)
}
```

#### GET Album by ID
```go
func getAlbumByID(c *gin.Context) {
    id := c.Param("id")
    for _, a := range albums {
        if a.ID == id {
            c.IndentedJSON(http.StatusOK, a)
            return
        }
    }
    c.IndentedJSON(http.StatusNotFound, gin.H{"message": "album not found"})
}
```

### 4. Run the Server
```bash
go run .
```
The server will start on `localhost:8084` (as configured in the code).

## Testing the API

### GET all albums
```bash
curl http://localhost:8084/albums
```

### POST a new album
```bash
curl http://localhost:8084/albums \
    --include \
    --header "Content-Type: application/json" \
    --request "POST" \
    --data '{"id": "4","title": "The Modern Sound of Betty Carter","artist": "Betty Carter","price": 49.99}'
```

### GET a specific album
```bash
curl http://localhost:8084/albums/2
```

---

> [!TIP]
> Use `c.IndentedJSON` for development to get pretty-printed output. In production, `c.JSON` is better for performance and smaller payloads.
