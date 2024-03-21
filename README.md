# [Microservice using Go, Chi & Redis](https://www.youtube.com/watch?v=wpnN3RIRSxs&list=PL4cUxeGkcC9iImF8w9FbFOc2UntutL9Wv&index=1)

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
docker run -p 6379:6379 redis:latest
```

```sh
python scripts/publish-orders.py
```

```sh
curl -sS "localhost:3000/orders"
curl -sS "localhost:3000/orders?cursor=39"
curl -sS "http://localhost:3000/orders/3806658213066379331"
```
