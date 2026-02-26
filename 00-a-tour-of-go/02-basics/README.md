# 🥪 Stop 2: Basics

![Gopher Coding](../../media/coding.png)

Now we're getting into the real stuff! The **Basics** section is like the Gopher's survival kit. We'll learn how to name things, how to make decisions, and how to store our carrots (data).

## 📍 Topics Covered

### 1. Packages, Variables, and Functions
Learn how to organize code and manage data types.
- **[01-packages.go](./01-packages-variables-and-functions/01-packages.go)**: Programs start in `package main`.
- **[04-functions.go](./01-packages-variables-and-functions/04-functions.go)**: Taking inputs and returning values.
- **[08-variables.go](./01-packages-variables-and-functions/08-variables.go)**: Using `var` to declare properties.
- **[11-basic-types.go](./01-packages-variables-and-functions/11-basic-types.go)**: `int`, `float64`, `string`, `bool`, etc.

### 2. Flow Control
How our Gopher decides what to do next.
- **[01-for.go](./02-flow-control/01-for.go)**: The only loop you'll ever need in Go.
- **[05-if.go](./02-flow-control/05-if.go)**: Conditional logic.
- **[09-switch.go](./02-flow-control/09-switch.go)**: A cleaner way for multiple conditions.
- **[12-defer.go](./02-flow-control/12-defer.go)**: Delaying an action until the function returns (super useful for cleanup!).

### 3. More Types: Structs, Slices, and Maps
Advanced ways to group and manage data.
- **[01-pointers.go](./03-more-types/01-pointers.go)**: Storing memory addresses.
- **[02-structs.go](./03-more-types/02-structs.go)**: Custom collections of fields.
- **[07-slices.go](./03-more-types/07-slices.go)**: Dynamically-sized arrays.
- **[19-maps.go](./03-more-types/19-maps.go)**: Key-value stores.

---

## 🏋️ Exercise Walkthroughs

### 1. Exercise: Loops and Functions
- **File**: `08-exercise-loops-and-functions.go`
- **Goal**: Implement a square root function using Newton's method.
- **Logic**: Use a `for` loop to iterate until the result stops changing significantly.

### 2. Exercise: Slices
- **File**: `18-exercise-slices.go`
- **Goal**: Implement `Pic(dx, dy int) [][]uint8`.
- **Logic**: Create a slice of slices, and for each pixel, calculate a value based on its coordinates (e.g., `x ^ y`).

### 3. Exercise: Maps
- **File**: `23-exercise-maps.go`
- **Goal**: Implement `WordCount`.
- **Logic**: Use `strings.Fields` to split the text and a map to count each occurrence.

### 4. Exercise: Fibonacci Closure
- **File**: `26-exercise-fibonacci-closure.go`
- **Goal**: Implement a function that returns a closure.
- **Logic**: The closure "remembers" the last two numbers to calculate the next one in the sequence.

> [!TIP]
> Remember: In Go, **less is more**. If you find yourself writing a complex `while` loop, try a simple `for`! 🐹💡
