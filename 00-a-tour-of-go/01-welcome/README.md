# 🏁 Stop 1: Welcome!

![Gopher Welcome](../../media/welcome.png)

Every adventure starts with a single step... or a single line of code! The **Welcome** section of the tour is about getting familiar with the environment and making sure our Gopher can say hi to the world.

## 📍 Topics Covered

1.  **Hello, World**: The universal greeting of programmers.
2.  **Using the Tour**: How to run code and see the output.

## 📝 Exercise: Hello, World
In [01-hello.go](./01-hello.go), we simply print a message.

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```

### Explanación (Gopher Style)
- `package main`: Le dice a Go que este archivo es la entrada principal de nuestro programa.
- `import "fmt"`: Trae el paquete de "formateo" para que podamos imprimir cosas.
- `fmt.Println`: Imprime el texto y añade una nueva línea al final. 

> [!NOTE]
> ¿Viste el `世界`? ¡Go soporta Unicode nativamente! Tu Gopher puede hablar cualquier idioma. 🐹🌍
