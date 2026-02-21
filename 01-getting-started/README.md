# 🏁 Phase 1: Get Started with Go - The Gopher Way

Welcome to the starting line! Before we build the next big thing, we need to teach our Gopher how to stand. 🐹

![Gopher Coding](./../media/coding.png)

In this first adventure, you will:

1.  **Install Go** (if you haven't already).
2.  **Write some simple "Hello, world" code**.
3.  **Use the `go` command** to run your code.
4.  **Use the Go package discovery tool** to find packages you can use in your own code.
5.  **Call functions of an external module**.

---

## Prerequisites

*   Some programming experience. The code here is simple, but knowing about functions helps.
*   A tool to edit your code (VSCode, GoLand, Vim, etc.).
*   A command terminal (Linux/Mac Terminal, PowerShell, or cmd).

---

## Step 1: Install Go

Please follow the official [Download and install](https://go.dev/doc/install) steps for your operating system.

---

## Step 2: Create Your First Project

### 1. Initialize your workspace
Open a command prompt and navigate to your home directory or desired workspace.

**On Linux or Mac:**
```bash
cd ~
```

**On Windows:**
```powershell
cd %HOMEPATH%
```

### 2. Create a directory for your code
Create a `hello` directory and move into it:
```bash
mkdir hello
cd hello
```

### 3. Enable dependency tracking
When you import packages from other modules, you manage those dependencies through your code's own module. This is defined by a `go.mod` file.

Run the `go mod init` command, giving it the name of your module. For this tutorial, we will use `comunidaddevops.com/hello`:

```bash
go mod init comunidaddevops.com/hello
```
> [!NOTE]
> In actual development, the module path is typically the repository location, e.g., `github.com/username/project`.

---

## Step 3: Write and Run "Hello, World"

### 1. Create the source file
In your text editor, create a file named `hello-world.go` and paste the following code:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

### 2. Breakdown of the code
*   `package main`: Declares the package. The `main` package is the entry point for Go applications.
*   `import "fmt"`: Imports the standard library package for formatting text.
*   `func main()`: Implements the function that executes by default when you run the package.

### 3. Run your code
In your terminal, run the following command to see the greeting:

```bash
go run .
```

---

## Step 4: Call Code in an External Package

When you need functionality implemented by others, you can search for packages on [pkg.go.dev](https://pkg.go.dev/).

### 1. Find a package
Visit [pkg.go.dev](https://pkg.go.dev/) and search for the `quote` package. We will use `rsc.io/quote`.

### 2. Update your code
Import the `rsc.io/quote` package and call its `Go()` function:

```go
package main

import (
    "fmt"
    "rsc.io/quote"
)

func main() {
    fmt.Println(quote.Go())
}
```

### 3. Add module requirements
Go needs to download the external module and track it in your `go.mod` file. Run:

```bash
go mod tidy
```
This command finds the module for the package you imported, downloads it, and updates your `go.mod` and `go.sum` files.

### 4. Run the updated code
```bash
go run .
```
You should see a clever message about shared memory!

---

## Summary and Next Steps

You've successfully:
- Installed Go.
- Created a module and wrote your first Go program.
- Explored external packages and managed dependencies.

For more advanced tutorials, visit the [official Go documentation](https://go.dev/doc/tutorial/create-module).