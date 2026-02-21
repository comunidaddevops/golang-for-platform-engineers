# Step 3: Return a Random Greeting

Instead of returning a single greeting every time, you'll update your code to return one of several predefined messages at random.

## Instructions

### 1. Update the greetings module
Modify `greetings/greetings.go` to include a helper function for random formats:

```go
package greetings

import (
    "errors"
    "fmt"
    "math/rand"
)

func Hello(name string) (string, error) {
    if name == "" {
        return name, errors.New("empty name")
    }
    // Call randomFormat to get a message template
    message := fmt.Sprintf(randomFormat(), name)
    return message, nil
}

func randomFormat() string {
    // A slice of message formats
    formats := []string{
        "Hi, %v. Welcome!",
        "Great to see you, %v!",
        "Hail, %v! Well met!",
    }

    return formats[rand.Intn(len(formats))]
}
```

### 2. Update the caller
Change `hello/hello.go` to pass a valid name:

```go
message, err := greetings.Hello("Gladys")
```

### 3. Run the code
Run the application multiple times to see the output change:
```bash
go run .
```

## Key Concepts
*   **Slices**: Like arrays but dynamically sized. Declared as `[]string`.
*   **Unexported Functions**: Functions starting with a lowercase letter (like `randomFormat`) are private to the package.
*   **math/rand**: Used for generating random numbers based on a seed or index.
