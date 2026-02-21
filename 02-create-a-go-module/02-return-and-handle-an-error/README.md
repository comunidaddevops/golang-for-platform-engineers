# Step 2: Return and Handle an Error

In this step, you'll update the `greetings` module to return an error if the name is empty, and then update the caller application to handle that error.

## Instructions

### 1. Update the greetings module
Modify `greetings/greetings.go` to handle empty names:

```go
package greetings

import (
    "errors"
    "fmt"
)

// Hello returns a greeting for the named person.
func Hello(name string) (string, error) {
    // If no name was given, return an error with a message.
    if name == "" {
        return "", errors.New("empty name")
    }

    // If a name was received, return a greeting message.
    message := fmt.Sprintf("Hi, %v. Welcome!", name)
    return message, nil
}
```

### 2. Create the caller application
Create a new directory named `hello` at the same level as `greetings`, then initialize it:

```bash
mkdir hello
cd hello
go mod init example.com/hello
```

### 3. Edit the caller application
Create `hello/hello.go` and add code to handle the error:

```go
package main

import (
    "fmt"
    "log"
    "example.com/greetings"
)

func main() {
    // Set log prefix and disable timestamp for cleaner output
    log.SetPrefix("greetings: ")
    log.SetFlags(0)

    // Request a greeting message with an empty string to trigger error
    message, err := greetings.Hello("")
    if err != nil {
        log.Fatal(err)
    }

    fmt.Println(message)
}
```

### 4. Link the modules locally
Since `example.com/greetings` isn't published, use the `go mod edit` command to point to the local directory:

```bash
cd hello
go mod edit -replace example.com/greetings=../greetings
go mod tidy
```

## Key Concepts
*   **Multiple Return Values**: Go functions can return more than one value (e.g., `(string, error)`).
*   **Error Handling**: It is idiomatic in Go to check `if err != nil` immediately after a function call.
*   **Log Package**: Used for reporting errors and stopping execution with `log.Fatal`.
*   **Replace Directive**: Allows you to use local modules that haven't been published yet.
