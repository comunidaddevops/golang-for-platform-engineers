# Step 1: Add Non-Generic Functions

In this step, you’ll add two functions that each add together the values of a map and return the total. You’re declaring two functions instead of one because you’re working with two different types of maps.

## Instructions

### 1. Implement specific sum functions
In `main.go`, we define one function for `int64` and another for `float64`:

```go
// SumInts adds together the values of m.
func SumInts(m map[string]int64) int64 {
    var s int64
    for _, v := range m {
        s += v
    }
    return s
}

// SumFloats adds together the values of m.
func SumFloats(m map[string]float64) float64 {
    var s float64
    for _, v := range m {
        s += v
    }
    return s
}
```

### 2. Call the functions
```go
ints := map[string]int64{"first": 34, "second": 12}
floats := map[string]float64{"first": 34.5, "second": 12.7}

fmt.Printf("Sums: %v and %v\n", SumInts(ints), SumFloats(floats))
```

## The Problem
Notice that the logic in `SumInts` and `SumFloats` is identical. The only difference is the type signature. This duplication is exactly what generics aim to solve.
