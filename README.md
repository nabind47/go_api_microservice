```go
func main() {
	server := &http.Server{
		Addr:    ":8000",
		Handler: http.HandlerFunc(basicHandler),
	}

	err := server.ListenAndServe()
	if err != nil {
		fmt.Println("Failed to listen and server", err)
	}
}

func basicHandler(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello World!"))
}
```

---

```go
func main() {
	router := chi.NewRouter()
	router.Use(middleware.Logger)

	router.Post("/", basicHandler)
	server := &http.Server{
		Addr:    ":8000",
		Handler: router,
	}

	err := server.ListenAndServe()
	if err != nil {
		fmt.Println("Failed to listen and server", err)
	}
}

func basicHandler(w http.ResponseWriter, r *http.Request) {
	w.Write([]byte("Hello World!"))
}
```

> [**_chi is a lightweight, idiomatic and composable router for building Go HTTP services. It's especially good at helping you write large REST API services that are kept maintainable as your project grows and changes._**](https://github.com/go-chi/chi)

```sh
curl http://localhost:8000
curl -X POST http://localhost:8000 -v
```

---

```sh
docker run -p 6379:6379 redis:latest
```
