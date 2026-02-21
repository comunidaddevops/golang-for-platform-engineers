# Step 3: Add a Fuzz Test

In this section, you will convert the unit test to a fuzz test to find edge cases that your unit test missed.

## Instructions

### 1. Convert to Fuzz Test
Replace your unit test with a fuzz test in `reverse_test.go`:

```go
func FuzzReverse(f *testing.F) {
    testcases := []string{"Hello, world", " ", "!12345"}
    for _, tc := range testcases {
        f.Add(tc) // Seed corpus
    }
    f.Fuzz(func(t *testing.T, orig string) {
        rev, err1 := Reverse(orig)
        if err1 != nil {
            return
        }
        doubleRev, err2 := Reverse(rev)
        if err2 != nil {
            return
        }
        if orig != doubleRev {
            t.Errorf("Before: %q, after: %q", orig, doubleRev)
        }
    })
}
```

### 2. Run the fuzzer
```bash
go test -fuzz=Fuzz
```

## Fixing Bugs

The fuzzer will likely find that reversing certain characters (like emojis or non-ASCII characters) produces invalid results when using byte slices.

### The Fix
Modify `main.go` to use **runes** instead of bytes and validate UTF-8:

```go
func Reverse(s string) (string, error) {
    if !utf8.ValidString(s) {
        return s, errors.New("input is not valid UTF-8")
    }
    r := []rune(s)
    for i, j := 0, len(r)-1; i < len(r)/2; i, j = i+1, j-1 {
        r[i], r[j] = r[j], r[i]
    }
    return string(r), nil
}
```

### 3. Verify the fix
Run the fuzzer again for a period of time:
```bash
go test -fuzz=Fuzz -fuzztime 30s
```

## Key Concepts
- **`f.Add`**: Adds a seed to the corpus.
- **`f.Fuzz`**: Runs the fuzzing engine with generated data.
- **Runes**: Represent Unicode code points. Crucial for handling multi-byte characters correctly.
- **Type Inference in Fuzzing**: The fuzzer automatically determines the type of the parameters to the fuzz target function.
