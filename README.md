# Moringa AI Capstone Project  
## Prompt-Powered Kickstart: Beginner’s Toolkit With Go (Golang)

This project is my Moringa School AI Capstone submission. The goal is to choose a new technology, learn it using AI prompt assistance, and produce a beginner-friendly toolkit that anyone can follow.  
I chose **Go (Golang)** because it’s simple, fast, and excellent for small CLI tools and tiny HTTP APIs.

This repository contains:

- **hello-go-cli** — a simple runnable Go CLI application  
- **hello-go-api** — a tiny Go HTTP API  
- **docs/toolkit.md** — the full beginner’s toolkit, prompts used, reflections, errors, and setup steps  
- Build instructions and troubleshooting notes

---

## Project Structure

moringa-capstone-go/
│
├── hello-go-cli/
│ ├── main.go
│ └── go.mod
│
├── hello-go-api/
│ ├── main.go
│ └── go.mod
│
├── docs/
│ └── toolkit.md
│
└── LICENSE
│
└── README.md

---

## Getting Started

### 1. Install Go

Check your OS instructions inside `docs/toolkit.md`, or use:

```bash
go version
```

### 2. Running the CLI app

```bash
cd hello-go-cli
go run main.go
go run main.go --name="YourName"
```

### Expected Output

```csharp
Hello, World! — from Go CLI
Hello, YourName! — from Go CLI
```

### 3. Running the API

```bash
cd hello-go-api
go run main.go
```

### API endpoints

```pgsql
GET /                -> "Hello from Go API"
GET /hello?name=Bob  -> "Hello, Bob! — from Go API"
```

### Browser test

```bash
curl http://localhost:8080/
curl "http://localhost:8080/hello?name=Bob"
```

## Build binaries

### CLI:

```bash
cd hello-go-cli
go build -o hello-cli
```

### API:

```bash
cd hello-go-api
go build -o hello-api
```

## Toolkit and Documentation

Full setup instructions, AI prompt journal, troubleshooting, and reflection are inside:

```bash
docs/toolkit.md
```

## Testing Notes

You should be able to clone this repository and run both examples successfully using only:

```go
go run main.go
```

## Author

Malcolm Kagolobya
Moringa School — AI Capstone Project
November 2025