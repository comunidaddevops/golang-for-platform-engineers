# 🧬 Phase 6: Getting started with generics

![Gopher Coding](./../media/coding.png)

Ever wanted a function that works for everyone? With generics, you can declare and use functions or types that are written to work with any of a set of types provided by calling code. 🐹✨

## Tutorial Sequence

The tutorial is divided into four stages:

1.  **[Add non-generic functions](./01-add-non-generic-functions/README.md)**: See the limitations of code without generics.
2.  **[Add a generic function](./02-add-a-generic-function-to-handle-multiple-types/README.md)**: Create a single function that handles multiple types using type parameters.
3.  **[Type Inference](./03-remove-type-arguments-when-calling-the-generic-function/README.md)**: Simplify calling code by letting the compiler infer types.
4.  **[Type Constraints](./04-declare-a-type-constraint/README.md)**: Define reusable interfaces as constraints for type parameters.

---

## Core Concepts

- **Type Parameters**: Declared in square brackets `[]` after the function or type name.
- **Type Constraints**: Interfaces that define the set of allowed types for a type parameter.
- **Comparable**: A built-in constraint for types that support `==` and `!=`.

---

> [!TIP]
> Generics were introduced in Go 1.18. Make sure your `go.mod` specifies at least `go 1.18` to use these features.
