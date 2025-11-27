# Prompt-Powered Kickstart: Getting Started With Go (Golang)
### Moringa School — AI Capstone Project

---

# 1. Title & Objective

**Title:** Getting Started with Go — CLI + Tiny API  
**Objective:**  
Use AI prompts to learn Go, set it up from scratch, build two minimal runnable examples, and create a beginner-friendly toolkit for future learners.

End goal:  
- A working **CLI app**  
- A working **HTTP API**  
- Clear documentation + AI prompt journal

---

# 2. Quick Summary of Go

Go (Golang) is a modern, statically typed, compiled programming language created by Google.  
It’s popular for:

- Web servers  
- Microservices  
- CLI tools  
- Networking tools  
- Cloud-native applications  

**Real-world use case:**  
Docker, Kubernetes, Terraform, and many modern cloud tools are built using Go.

---

# 3. System Requirements

- **OS:** Windows, macOS, or Linux  
- **Tools:**  
  - Go (latest version)  
  - VS Code (recommended)  
  - Git (optional but recommended)  
- **Port:** 8080 (for the API example)

---

# 4. Installation & Setup Instructions

### Check if Go is installed:

```bash
go version
```

If Go prints a version → ready.
If not, install using instructions below:

## MacOS

```bash
brew install go
```

## Linux/Ubuntu

```bash
sudo apt update
sudo apt install -y golang
```

## Windows

Download installer from: https://go.dev/dl

or

Using Chocolatey:

```powershell
choco install golang
```

### Verify installation

```bash
go version
```

### Expected sample output

```bash
go version go1.22.2 linux/amd64
```

# 5. Minimal Working Examples

# A. CLI App — hello-go-cli

### File: hello-go-cli/main.go

```go
package main

import (
	"flag"
	"fmt"
)

func main() {
	name := flag.String("name", "World", "name to greet")
	flag.Parse()

	fmt.Printf("Hello, %s! — from Go CLI\n", *name)
}
```

## Run it

```bash
cd hello-go-cli
go run main.go
go run main.go --name="Malcolm"
```

## Expected Output

```csharp
Hello, World! — from Go CLI
Hello, Malcolm! — from Go CLI
```

# B. Tiny HTTP API — hello-go-api

### File: hello-go-api/main.go

```go
package main

import (
	"fmt"
	"net/http"
)

func helloHandler(w http.ResponseWriter, r *http.Request) {
	name := r.URL.Query().Get("name")
	if name == "" {
		name = "World"
	}
	fmt.Fprintf(w, "Hello, %s! — from Go API\n", name)
}

func rootHandler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintln(w, "Hello from Go API")
}

func main() {
	http.HandleFunc("/", rootHandler)
	http.HandleFunc("/hello", helloHandler)

	addr := ":8080"
	fmt.Println("Server running on http://localhost" + addr)
	if err := http.ListenAndServe(addr, nil); err != nil {
		fmt.Println("Server error:", err)
	}
}
```

## Run the API:

```bash
cd hello-go-api
go run main.go
```

## Test with curl

```bash
curl http://localhost:8080/
curl "http://localhost:8080/hello?name=Malcolm"
```

# 6. AI Prompt Journal

Below are the prompts used during development.
Each includes the prompt, a short summary of the AI’s response, and a reflection.

---

### Prompt 1: Learning plan

Prompt:
"I want to learn the Go programming language as a beginner using step-by-step guidance. Give me a plan to produce a CLI app and tiny API."

AI Summary:
Provided structured steps: install Go → create CLI → create API → build binaries → document everything.

Reflection:
Gave me clarity on the entire workflow from the start.

---

### Prompt 2: Installation help

Prompt:
"Explain how to install Go on Windows/Linux/Mac. Include commands and how to verify installation."

AI Summary:
Gave OS-specific commands + verification instructions.

Reflection:
I copied the commands directly; installation became easy.

---

### Prompt 3: CLI program

Prompt:
"Give me a simple Go CLI program that prints Hello <name> using flag parsing."

AI Summary:
AI wrote the exact code and explained every line.

Reflection:
Excellent — worked on first try.

---

### Prompt 4: API server

Prompt:
"Show a minimal Go HTTP server that responds at '/' and '/hello?name='."

AI Summary:
Provided a working main.go and curl commands to test.

Reflection:
Made building an API much faster.

---

### Prompt 5: Troubleshooting PATH errors

Prompt:
"I'm getting 'go: command not found'. How do I fix PATH issues?"

AI Summary:
Explained how to update PATH for all OSes.

Reflection:
Solved my installation issue.

---

### Prompt 6: Documentation help

Prompt:
"Help me write a Toolkit Document summarizing steps, examples, AI prompts, and reflections."

AI Summary:
Gave a structure which I adapted for this file.

Reflection:
Made documentation clean and readable.

# 7. Common Issues & Fixes

Problem: go: command not found

Fix: Add Go’s bin folder to PATH.

mac/Linux: 

export PATH=$PATH:/usr/local/go/bin

Windows: 

Edit Environment Variables → Path.

Problem: Port 8080 already in use

Fix:

mac/linux

```bash
lsof -i :8080
kill -9 <PID>
```

windows

```powershell
netstat -ano | findstr :8080
taskkill /PID <PID> /F
```

Problem: module errors

Fix:

```bash
go mod tidy
```