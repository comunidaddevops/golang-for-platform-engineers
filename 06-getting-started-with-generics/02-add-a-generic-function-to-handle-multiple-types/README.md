# Step 2: Add a Generic Function

In this section, you’ll add a single generic function that can receive a map containing either integer or float values, replacing the previous two functions.

## Instructions

### 1. Declare the generic function
Use square brackets `[]` to declare type parameters:

```go
func SumIntsOrFloats[K comparable, V int64 | float64](m map[K]V) V {
    var s V
    for _, v := range m {
        s += v
    }
    return s
}
```

### 2. Call the function with type arguments
When calling the function, you specify the concrete types in brackets:

```go
fmt.Printf("Generic Sums: %v and %v\n",
    SumIntsOrFloats[string, int64](ints),
    SumIntsOrFloats[string, float64](floats))
```

## Key Concepts

- **Type Parameters**: `K` and `V` are placeholders for types.
- **`comparable` Constraint**: A built-in constraint for map keys.
- **Union Type Constraint**: `int64 | float64` allows either type for the values.
- **Type Safety**: The compiler ensures that the provided types match the constraints.
