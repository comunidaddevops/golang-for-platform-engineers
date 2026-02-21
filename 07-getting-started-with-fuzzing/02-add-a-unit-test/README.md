# Step 2: Add a Unit Test

In this step, you’ll write a standard unit test for the `Reverse` function.

## Instructions

### 1. Create the test file
Create `reverse_test.go` with a table-driven test:

```go
package main

import (
    "testing"
)

func TestReverse(t *testing.T) {
    testcases := []struct {
        in, want string
    }{
        {"Hello, world", "dlrow ,olleH"},
        {" ", " "},
        {"!12345", "54321!"},
    }
    for _, tc := range testcases {
        rev := Reverse(tc.in)
        if rev != tc.want {
            t.Errorf("Reverse: %q, want %q", rev, tc.want)
        }
    }
}
```

### 2. Run the test
```bash
go test
```

## Limitations
Unit tests only test the inputs provided by the developer. They are great for regression testing but might miss unexpected edge cases, especially when dealing with complex data like UTF-8 strings.
