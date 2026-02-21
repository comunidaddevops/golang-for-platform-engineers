# Step 1: Create a Go Module

In this step, you'll create a Go module named `greetings`. This module will serve as a library with a single function, `Hello`, which returns a greeting message.

## Prerequisites
*   Go installed on your machine.
*   A code editor and a terminal.

## Instructions

### 1. Create a directory for your module
```bash
mkdir greetings
cd greetings
```

### 2. Initialize the module
Run the `go mod init` command with your chosen module path. For this tutorial, we use `example.com/greetings`:

```bash
go mod init example.com/greetings
```
This creates a `go.mod` file to track dependencies.

### 3. Create the source file
Create a file named `greetings.go` and paste the following code:

```go
package greetings

import "fmt"

// Hello returns a greeting for the named person.
func Hello(name string) string {
    // Return a greeting that embeds the name in a message.
    message := fmt.Sprintf("Hi, %v. Welcome!", name)
    return message
}
```

## Key Concepts
*   **Packages**: Go code is organized into packages. The `greetings` package will contain our greeting logic.
*   **Exported Names**: In Go, functions starting with a **capital letter** (like `Hello`) are exported and can be called from other packages.
*   **Sprintf**: Used to format strings. The `%v` is a "verb" that Go replaces with the value of the `name` variable.
