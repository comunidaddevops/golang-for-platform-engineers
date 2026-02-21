# 💥 Phase 7: Getting started with fuzzing

![Gopher Coding](./../media/coding.png)

This tutorial introduces the basics of fuzzing in Go. Time to throw some digital tantrums at your code to see if it breaks! Fuzzing runs random data against your tests to find bugs before the real-world users do. 🐹💥

## Tutorial Sequence

The tutorial is divided into three stages:

1.  **[Add code to test](./01-add-code-to-test/README.md)**: Implement a simple string reversal function.
2.  **[Add a unit test](./02-add-a-unit-test/README.md)**: Write a standard Go unit test for the function.
3.  **[Add a fuzz test](./03-add-a-fuzz-test/README.md)**: Convert the unit test to a fuzz test and fix the bugs it discovers.

---

## Core Concepts

- **Fuzzing**: A type of automated testing which continuously provides random and invalid inputs to a program to find bugs.
- **Seed Corpus**: A set of user-provided inputs to the fuzzer that it uses as a starting point to generate new inputs.
- **Fuzz Target**: The function that is executed with fuzzed data.

---

> [!IMPORTANT]
> Fuzzing can consume a lot of memory and may affect your machine’s performance while it’s running. Be aware of your system resources.
