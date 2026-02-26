# 🤹 Stop 5: Concurrency

![Gopher Coding](../../media/coding.png)

Welcome to the big show! **Concurrency** is one of Go's most powerful features. It’s like having 100 Gophers working together on a project without bumping into each other.

## 📍 Topics Covered

### 1. Goroutines
Lightweight threads managed by the Go runtime.
- **[01-goroutines.go](./01-goroutines.go)**: Starting a task with `go f(x, y, z)`.

### 2. Channels
The pipes that connect goroutines. They allow you to send and receive values.
- **[02-channels.go](./02-channels.go)**: Using `<-` to send/receive data.
- **[03-buffered-channels.go](./03-buffered-channels.go)**: Channels with a capacity.

### 3. Select and Ranges
- **[04-range-and-close.go](./04-range-and-close.go)**: Closing channels and using `range` to receive until they close.
- **[05-select.go](./05-select.go)**: Letting a goroutine wait on multiple communication operations.

### 4. Mutual Exclusion (Mutex)
When you don't need communication, but just need to ensure only one Gopher is touching a piece of data at a time.
- **[08-mutex-counter.go](./08-mutex-counter.go)**: Using `sync.Mutex` with `Lock` and `Unlock`.

---

## 🏋️ Exercise Walkthroughs

### 1. Exercise: Equivalent Binary Trees
- **File**: `07-exercise-equivalent-binary-trees.go`
- **Goal**: Use channels to compare the contents of two binary trees.
- **Logic**: Use a goroutine to walk each tree and send its values into a channel. Then, compare the values coming out of both channels.

### 2. Exercise: Web Crawler
- **File**: `09-exercise-web-crawler.go`
- **Goal**: Make a web crawler use goroutines to fetch URLs in parallel.
- **Logic**: 
    - Use a map to track which URLs have already been fetched (use a Mutex to protect this map!).
    - Start a new goroutine for each new URL found.
    - Use a `sync.WaitGroup` or a channel to wait for all crawlers to finish.

---

## 🐹 Explanación (Gopher Style)

In Go, we have a famous saying:
> "Do not communicate by sharing memory; instead, share memory by communicating."

This means instead of using complex locks for everything, we use **channels** to pass data around. It's much safer and keeps our Gophers happy!

> [!CAUTION]
> Watch out for **Deadlocks**! If a Gopher is waiting for a message that will never come, he'll wait forever. Always make sure someone is on the other end of the pipe! 🐹🚫🚿
