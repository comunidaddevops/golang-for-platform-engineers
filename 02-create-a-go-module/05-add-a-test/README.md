# Step 5: Add a Test

Testing is a core part of the Go development workflow. You'll add unit tests to verify your greeting logic.

## Instructions

### 1. Create the test file
In the `greetings` directory, create `greetings_test.go`:

```go
package greetings

import (
    "testing"
    "regexp"
)

// TestHelloName calls greetings.Hello with a name, checking for valid return
func TestHelloName(t *testing.T) {
    name := "Gladys"
    want := regexp.MustCompile(`\b`+name+`\b`)
    msg, err := Hello("Gladys")
    if !want.MatchString(msg) || err != nil {
        t.Errorf(`Hello("Gladys") = %q, %v, want match for %#q, nil`, msg, err, want)
    }
}

// TestHelloEmpty calls greetings.Hello with an empty string, checking for error
func TestHelloEmpty(t *testing.T) {
    msg, err := Hello("")
    if msg != "" || err == nil {
        t.Errorf(`Hello("") = %q, %v, want "", error`, msg, err)
    }
}
```

### 2. Run the tests
From the terminal in the `greetings` directory:
```bash
go test
```
To see verbose output:
```bash
go test -v
```

## Key Concepts
*   **Testing Package**: Go's built-in `testing` package provides tools for writing and running tests.
*   **Naming Convention**: Test files must end in `_test.go`, and test functions must start with `Test` (e.g., `TestHelloName`).
*   **Error Reporting**: Use `t.Errorf` to report failures without stopping the entire test suite.
