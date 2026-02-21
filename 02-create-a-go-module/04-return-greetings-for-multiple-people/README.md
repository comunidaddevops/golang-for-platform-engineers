# Step 4: Return Greetings for Multiple People

In this step, you'll add support for getting greetings for multiple people in a single request using a Go map.

## Instructions

### 1. Update the greetings module
Add the `Hellos` function to `greetings/greetings.go`:

```go
// Hellos returns a map that associates each of the named people
// with a greeting message.
func Hellos(names []string) (map[string]string, error) {
    messages := make(map[string]string)
    
    // Loop through the slice of names
    for _, name := range names {
        message, err := Hello(name)
        if err != nil {
            return nil, err
        }
        messages[name] = message
    }
    return messages, nil
}
```

### 2. Update the caller
Modify `hello/hello.go` to use the new `Hellos` function:

```go
func main() {
    log.SetPrefix("greetings: ")
    log.SetFlags(0)

    // A slice of names
    names := []string{"Gladys", "Samantha", "Darrin"}

    // Request greetings for the names
    messages, err := greetings.Hellos(names)
    if err != nil {
        log.Fatal(err)
    }
    fmt.Println(messages)
}
```

## Key Concepts
*   **Maps**: A built-in data structure that stores key-value pairs (e.g., `map[string]string`).
*   **For Loops with Range**: `range` returns both the index and the value. We use the blank identifier `_` to ignore the index.
*   **make()**: Used to initialize a map before using it.
