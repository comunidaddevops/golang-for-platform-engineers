# Step 3: Type Inference

In many cases, the Go compiler can infer the type arguments from the function arguments, allowing you to omit the bracketed type names.

## Instructions

### 1. Simplify the call
Instead of writing `SumIntsOrFloats[string, int64](ints)`, you can simply write:

```go
fmt.Printf("Sums (Inferred): %v and %v\n",
    SumIntsOrFloats(ints),
    SumIntsOrFloats(floats))
```

## How it works
The compiler looks at the types of the arguments passed to the function (`ints` is `map[string]int64`) and determines that `K` must be `string` and `V` must be `int64`.

> [!NOTE]
> Type inference isn't always possible (e.g., functions with no arguments or ambiguous types). In those cases, you must provide the type arguments explicitly.
