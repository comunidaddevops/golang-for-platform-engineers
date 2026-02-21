# Step 1: Add Code to Test

In this step, you’ll add a function to reverse a string.

## Instructions

### 1. Implement the Reverse function
In `main.go`, we implement a simple reversal using a byte slice:

```go
func Reverse(s string) string {
    b := []byte(s)
    for i, j := 0, len(b)-1; i < len(b)/2; i, j = i+1, j-1 {
        b[i], b[j] = b[j], b[i]
    }
    return string(b)
}
```

### 2. Run the code
```bash
go run .
```

## Key Concepts
- **Byte Slices**: The initial implementation treats the string as a sequence of bytes. This works fine for basic ASCII characters but will fail for multi-byte characters (like accented letters or emojis), which we will discover later with fuzzing.
