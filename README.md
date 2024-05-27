# golang socket.io client

## example
```go
package main

import (
	"fmt"
	"net/http"
	"time"

	socketio "github.com/leviathan-1776/socketio-client-go"
)

func main() {
	var header http.Header = map[string][]string{}
	s, err := socketio.Socket("ws://127.0.0.1:3000")
	if err != nil {
		panic(err)
	}
	s.Connect(header)
	s.On("message", func(args ...interface{}) {
		fmt.Println(args[0])
	})
	for {
		s.Emit("message", "hello server!")
		time.Sleep(2 * time.Second)
	}
}

```

## server

* [socket.io](https://socket.io/)
* [go-socket.io](https://github.com/googollee/go-socket.io)

