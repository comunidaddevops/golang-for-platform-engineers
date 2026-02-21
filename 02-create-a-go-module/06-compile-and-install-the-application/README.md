# Step 6: Compile and Install the Application

In this final step, you'll learn how to build a binary executable and install it so you can run it from anywhere.

## Instructions

### 1. Build the executable
Navigate to your `hello` directory and run:

```bash
go build
```
This generates a `hello` (or `hello.exe`) file in the current directory.

### 2. Run the binary
```bash
./hello
```

### 3. Discover the install path
Find where Go installs binaries by default:
```bash
go list -f '{{.Target}}'
```

### 4. Add the path to your environment
To run the command from any terminal, add the path to your shell's `PATH`:

**On Linux or Mac:**
```bash
export PATH=$PATH:/path/to/your/install/directory
```

**Alternative (GOBIN):**
```bash
go env -w GOBIN=/path/to/your/bin
```

### 5. Install the package
```bash
go install
```
Now you can run `hello` from any directory!

## Key Concepts
*   **go build**: Compiles the code but doesn't install it in the system.
*   **go install**: Compiles and moves the binary to the Go bin directory (`$GOPATH/bin` or `$GOBIN`).
*   **Shell PATH**: An environment variable that tells the system where to look for executables.
