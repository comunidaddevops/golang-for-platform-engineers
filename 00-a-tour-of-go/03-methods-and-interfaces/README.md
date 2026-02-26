# ✨ Stop 3: Methods and Interfaces

![Gopher Coding](../../media/coding.png)

Welcome to the heart of Go's design! This is where we learn how to give our Gophers special abilities (methods) and how to define contracts (interfaces) that different Gophers can follow.

## 📍 Topics Covered

### 1. Methods
Functions with a "receiver" argument.
- **[01-methods.go](./01-methods.go)**: Defining methods on structs.
- **[04-methods-pointers.go](./04-methods-pointers.go)**: Why we usually use pointer receivers (to modify the original value).

### 2. Interfaces
Naming sets of method signatures.
- **[09-interfaces.go](./09-interfaces.go)**: An interface is satisfied implicitly. No `implements` keyword needed!
- **[14-empty-interface.go](./14-empty-interface.go)**: `interface{}` can hold values of any type.
- **[15-type-assertions.go](./15-type-assertions.go)**: Checking if an interface value holds a specific type.

### 3. Standards & Built-ins
- **[17-stringer.go](./17-stringer.go)**: Making your types printable with `String()`.
- **[19-errors.go](./19-errors.go)**: Custom error handling.
- **[21-reader.go](./21-reader.go)**: Streaming data.
- **[24-images.go](./24-images.go)**: Graphics and images.

---

## 🏋️ Exercise Walkthroughs

### 1. Exercise: Stringer
- **File**: `18-exercise-stringer.go`
- **Goal**: Make a `IPAddr` type printable as `127.0.0.1` instead of `[127 0 0 1]`.
- **Logic**: Implement the `fmt.Stringer` interface by adding a `String() string` method to the type.

### 2. Exercise: Errors
- **File**: `20-exercise-errors.go`
- **Goal**: Add error handling to your square root function.
- **Logic**: Create a custom type `ErrNegativeSqrt` and implement the `Error() string` method. Return this error if the input is negative.

### 3. Exercise: Readers
- **File**: `22-exercise-reader.go`
- **Goal**: Implement a `Reader` that emits an infinite stream of the ASCII character 'A'.
- **Logic**: Implement `Read(b []byte) (int, error)` by filling the slice `b` with `'A'` and returning the length.

### 4. Exercise: rot13Reader
- **File**: `23-exercise-rot-reader.go`
- **Goal**: Implement a `rot13Reader` that wraps an `io.Reader` and decodes it.
- **Logic**: The `Read` method calls the underlying reader and then transforms each byte according to the ROT13 cipher.

### 5. Exercise: Images
- **File**: `25-exercise-images.go`
- **Goal**: Implement your own image type.
- **Logic**: Implement the `image.Image` interface: `ColorModel()`, `Bounds()`, and `At(x, y)`.

> [!IMPORTANT]
> Interfaces in Go are **implicit**. If your type has the required methods, it *is* an implementation of that interface. No paperwork required! 🐹📜
