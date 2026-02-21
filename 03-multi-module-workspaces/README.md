# 🏗️ Phase 3: Getting started with multi-module workspaces

![Gopher Coding](./../media/coding.png)

This tutorial introduces the basics of multi-module workspaces in Go. With multi-module workspaces, you can tell the Go command that you’re writing code in multiple modules at the same time and easily build and run code in those modules. 🤹

In this tutorial, you’ll create two modules in a shared multi-module workspace, make changes across the modules, and see the results of those changes in a build.

---

## Prerequisites

- **Go 1.18 or later** installed.
- A command terminal and a code editor.

---

## Step 1: Create a module for your code

### 1. Initialize your directory
```bash
mkdir workspace
cd workspace
```

### 2. Create the `hello` module
Create a module that will depend on an external package:

```bash
mkdir hello
cd hello
go mod init example.com/hello
```

### 3. Add a dependency
Use `go get` to add the `reverse` package as a dependency:
```bash
go get golang.org/x/example/hello/reverse
```

### 4. Create `hello.go`
Create the file with the following content:

```go
package main

import (
    "fmt"
    "golang.org/x/example/hello/reverse"
)

func main() {
    fmt.Println(reverse.String("Hello"))
}
```

### 5. Run the program
```bash
go run .
# Output: olleH
```

---

## Step 2: Create the workspace

Now we will create a `go.work` file to specify a workspace that includes our `hello` module.

### 1. Initialize the workspace
In the `workspace` directory (one level up from `hello`), run:

```bash
go work init ./hello
```

The `go work init` command creates a `go.work` file that looks like this:

```go
go 1.18

use ./hello
```

### 2. Run the program from the workspace
Now you can run your program from the workspace root:

```bash
go run ./hello
```

---

## Step 3: Download and modify an external module

In this step, we’ll download the source code for the `golang.org/x/example/hello` module, add it to our workspace, and modify it locally.

### 1. Clone the repository
From the `workspace` directory:
```bash
git clone https://go.googlesource.com/example
```

### 2. Add the module to the workspace
The source for the module is in `./example/hello`. Add it:

```bash
go work use ./example/hello
```

Your `go.work` file should now look like this:

```go
go 1.18

use (
    ./hello
    ./example/hello
)
```

### 3. Add a new function locally
Create `example/hello/reverse/int.go` with a new function to reverse integers:

```go
package reverse

import "strconv"

// Int returns the decimal reversal of the integer i.
func Int(i int) int {
    i, _ = strconv.Atoi(String(strconv.Itoa(i)))
    return i
}
```

### 4. Use the new function in `hello`
Update `hello/hello.go` to use `reverse.Int`:

```go
package main

import (
    "fmt"
    "golang.org/x/example/hello/reverse"
)

func main() {
    fmt.Println(reverse.String("Hello"), reverse.Int(24601))
}
```

### 5. Run the program
```bash
go run ./hello
# Output: olleH 10642
```

The Go command now uses the **local** version of the `reverse` package instead of the one in your module cache!

---

## Key Commands Summary

| Command | Description |
| :--- | :--- |
| `go work init` | Initializes a workspace file (`go.work`). |
| `go work use [dir]` | Adds a module directory to the workspace. |
| `go work sync` | Syncs the workspace's build list to its modules. |
| `go env GOWORK` | Shows the path to the current `go.work` file. |

---

> [!TIP]
> Workspaces are perfect for making changes to multiple related modules simultaneously without having to publish them or use `replace` directives in every `go.mod` file.
