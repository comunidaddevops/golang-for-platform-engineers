# Tutorial: Create a Go Module

![Gopher Coding](./../media/coding.png)

This tutorial series introduces fundamental features of the Go language. You'll create two modules: a library (`greetings`) and a caller application (`hello`) that uses the library.

## Tutorial Sequence

The tutorial is divided into seven brief topics, each illustrating a different part of the language:

1.  **[Create a module](./01-create-a-module/README.md)**: Write a small module with functions you can call from another module.
2.  **Call your code from another module**: Import and use your new module (integrated into subsequent steps).
3.  **[Return and handle an error](./02-return-and-handle-an-error/README.md)**: Add simple error handling.
4.  **[Return a random greeting](./03-return-a-random-greeting/README.md)**: Handle data in slices (Go's dynamically-sized arrays).
5.  **[Return greetings for multiple people](./04-return-greetings-for-multiple-people/README.md)**: Store key/value pairs in a map.
6.  **[Add a test](./05-add-a-test/README.md)**: Use Go's built-in unit testing features.
7.  **[Compile and install the application](./06-compile-and-install-the-application/README.md)**: Compile and install your code locally.

---

## Prerequisites

*   **Some programming experience**: Basic knowledge of functions, loops, and arrays.
*   **A code editor**: VSCode (recommended), GoLand, or Vim.
*   **A command terminal**: Linux/Mac Terminal, PowerShell, or CMD.

---

> [!TIP]
> Each directory in this series represents a stage in the development of the `greetings` module and the `hello` caller application. Follow them in order to see the evolution of the code.