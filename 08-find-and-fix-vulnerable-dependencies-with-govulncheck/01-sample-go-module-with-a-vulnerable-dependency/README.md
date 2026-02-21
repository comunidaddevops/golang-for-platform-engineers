# Step 1: Create and Analyze a Vulnerable Module

In this step, you’ll set up a Go module with a known vulnerability and use `govulncheck` to find it.

## Instructions

### 1. Initialize the module
Create a module named `vuln.tutorial`:
```bash
go mod init vuln.tutorial
```

### 2. Add vulnerable code
In `main.go`, we use the `language` package from `golang.org/x/text`:

```go
package main

import (
    "fmt"
    "os"
    "golang.org/x/text/language"
)

func main() {
    for _, arg := range os.Args[1:] {
        tag, err := language.Parse(arg)
        if err != nil {
            fmt.Printf("%s: error: %v\n", arg, err)
        } else {
            fmt.Printf("%s: tag %s\n", arg, tag)
        }
    }
}
```

### 3. Downgrade to a vulnerable version
To simulate a real scenario, we'll use an old version of the package:
```bash
go mod tidy
go get golang.org/x/text@v0.3.5
```

### 4. Install and run govulncheck
Install the tool:
```bash
go install golang.org/x/vuln/cmd/govulncheck@latest
```

Run the scan:
```bash
govulncheck ./...
```

## Interpreting the Output
`govulncheck` will identify **GO-2021-0113**: an out-of-bounds read in `golang.org/x/text/language` that can cause a panic. Because our code calls `language.Parse`, the tool correctly flags this as an affecting vulnerability.

---

> [!IMPORTANT]
> If a vulnerability exists in a package you import but you don't call the affected function, `govulncheck` will list it as "Informational," as it doesn't affect your specific binary.
