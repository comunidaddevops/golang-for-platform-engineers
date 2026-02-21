# Step 4: Declare a Type Constraint

You can move complex type constraints into their own interface to make your code more readable and reusable.

## Instructions

### 1. Define the Constraint
Use an interface to define a union of types:

```go
type Number interface {
    int64 | float64
}
```

### 2. Use the Constraint in the function
Replace the inline union with the interface name:

```go
func SumNumbers[K comparable, V Number](m map[K]V) V {
    var s V
    for _, v := range m {
        s += v
    }
    return s
}
```

### 3. Call the final version
```go
fmt.Printf("Sums with Interface: %v and %v\n",
    SumNumbers(ints),
    SumNumbers(floats))
```

## Summary
Declaring constraints as interfaces is a powerful pattern in Go. It allows you to group related types and reuse the constraint across multiple functions or structures.
