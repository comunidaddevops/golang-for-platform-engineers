# 🧬 Stop 4: Generics

![Gopher Coding](../../media/coding.png)

The newest addition to the Gopher's toolkit! **Generics** allow us to write code that is flexible and works with many types without losing type safety.

## 📍 Topics Covered

### 1. Type Parameters
- **[01-index.go](./01-index.go)**: A generic function to find the index of a value in a slice of any comparable type.

### 2. Generic Types
- **[02-list.go](./02-list.go)**: Implementing a generic linked list.

---

## 🐹 Explanación (Gopher Style)

Generics use **Type Parameters** inside square brackets `[T any]`. 

For example, a generic list:
```go
type List[T any] struct {
	next *List[T]
	val  T
}
```

This means `T` can be an `int`, a `string`, or even another `Gopher` struct!

> [!NOTE]
> Generics make code more reusable, but use them wisely! If a simple slice or interface does the job, you might not need a generic. 🐹🧠
