# 🗺️ Go — 6 Month Learning Roadmap

> **2 sessions/week:** 🌐 Online (theory & concepts) + 🏠 Offline (exercises & project work)
> **6 projects:** go-reloaded → ascii-art → ascii-art-web → groupie-tracker → lem-in → forum

---

## Overview

| Month | Project | Core Skills |
|-------|---------|-------------|
| 1 | go-reloaded | Files, strings, functions, error handling |
| 2 | ascii-art | File parsing, data structures, 2D arrays |
| 3 | ascii-art-web | HTTP server, HTML templates, Go web basics |
| 4 | groupie-tracker | APIs, JSON, client-server, events |
| 5 | lem-in | Graphs, algorithms, pathfinding (BFS) |
| 6 | forum | SQL, auth, cookies, sessions, Docker |

---

---

# 📅 Month 1 — go-reloaded
> **Goal:** Build a text auto-correction CLI tool
> **Teaches:** File I/O, string manipulation, functions, error handling, `os.Args`

---

### Week 1 — Foundations for the Project

**🌐 Online — Functions & Error Handling**
- Defining and calling functions, multiple return values
- The `error` type — returning and checking errors
- `fmt.Errorf`, `errors.New`
- Why Go doesn't use exceptions
- Live demo: a function that divides two numbers and returns an error on division by zero

**🏠 Offline — Go Gladiators Session 1** *(already planned)*
- Round 1: Username Formatter
- Round 2: Vault Decoder
- Round 3: Log Auditor
- Round 4: Broken Dialogue Fixer

---

### Week 2 — String Manipulation Deep Dive

**🌐 Online — The `strings` Package**
- `strings.Split`, `strings.Join`, `strings.Fields`
- `strings.Replace`, `strings.ReplaceAll`, `strings.Contains`
- `strings.ToUpper`, `strings.ToLower`, `strings.Title`
- `strings.TrimSpace`, `strings.Index`
- `strconv.ParseInt` with bases (2, 16) + `strconv.Itoa`
- Live demo: detect and convert `(hex)` and `(bin)` markers in a sentence

**🏠 Offline — String Challenges**
- Challenge 1: Given a messy sentence, fix all spacing around punctuation `. , ! ? : ;`
- Challenge 2: Parse `(up, 3)` style commands and apply them to N previous words
- Challenge 3: Replace `a` with `an` before vowels and `h`
- Mini-project start: students scaffold their `main.go` with `os.Args` reading

---

### Week 3 — File I/O + Project Completion

**🌐 Online — The `os` and `bufio` Packages**
- `os.Open`, `os.Create`, `os.ReadFile`, `os.WriteFile`
- `bufio.Scanner` for line-by-line reading
- `bufio.Writer` + `Flush()`
- `defer` — when and why to use it
- `os.Args` — reading command-line arguments
- Live demo: read a file, transform each line, write to a new file

**🏠 Offline — go-reloaded Project Session**
- Students work on the full project
- Facilitator focuses on: quote `'...'` formatting edge cases and the `(cap, N)` logic
- Peer code review at the end: each student reads one classmate's code
- Unit test writing: test at least 2 transformation functions

---

---

# 📅 Month 2 — ascii-art
> **Goal:** Render strings as ASCII art using banner files
> **Teaches:** File parsing, 2D character grids, runes vs bytes, indexing

---

### Week 4 — Runes, Bytes & ASCII

**🌐 Online — Characters in Go**
- `byte` vs `rune` — why it matters
- Iterating strings with `range` vs index
- ASCII table — how characters map to numbers
- How the banner files are structured (8 lines per character, separated by `\n`)
- Live demo: read the `standard.txt` banner and print the 8 lines for the letter `A`

**🏠 Offline — Banner Parsing Challenges**
- Challenge 1: Read `standard.txt` and store each character's 8 lines in a `map[rune][]string`
- Challenge 2: Given the map, print the word `"Hi"` in ASCII art
- Challenge 3: Handle `\n` in input — split into multiple lines and print each

---

### Week 5 — 2D Output + Edge Cases

**🌐 Online — Building Output Row by Row**
- How to print multiple characters side by side (iterate rows 0–7, print all chars per row)
- Handling spaces — space is ASCII 32, it has its own entry in the banner
- Handling empty input and `\n` only input
- Live demo: render `"Hello World"` correctly with spaces between words

**🏠 Offline — ascii-art Project Session**
- Students complete the full ascii-art project
- Edge case focus: `""`, `"\n"`, `"\n\n"`, special characters like `{`, `}`
- Facilitator challenge: who can render `"Go Zone!"` first with all 3 banners
- Unit tests: test that `"Hello"` produces the exact expected output

---

### Week 6 — Review + Good Practices

**🌐 Online — Writing Clean Go Code**
- Naming conventions: variables, functions, packages
- Short functions — single responsibility
- Comments and documentation (`// comment`, `/* */`, `godoc`)
- `go fmt`, `go vet` — automated code hygiene
- Package structure: when to split into multiple files

**🏠 Offline — Code Refactor Session**
- Students refactor their ascii-art code using good practices
- Split into: `parser.go`, `renderer.go`, `main.go`
- Peer review: each student gives written feedback on one classmate's structure
- Discuss: what would break if the banner format changed?

---

---

# 📅 Month 3 — ascii-art-web
> **Goal:** Serve ascii-art through a web interface
> **Teaches:** HTTP, Go templates, HTML basics, status codes, routing

---

### Week 7 — How the Web Works

**🌐 Online — HTTP Fundamentals**
- Request / Response cycle
- HTTP methods: `GET` vs `POST`
- Status codes: `200`, `400`, `404`, `500`
- Headers and body
- What happens when you type a URL in a browser
- Live demo: `curl` a website, inspect headers

**🏠 Offline — HTML Basics Crash Course**
- Build a simple HTML page with: text input, radio buttons, a submit button
- Style it minimally with inline CSS (no frameworks)
- Challenge: build the exact UI needed for ascii-art-web by hand, no server yet
- Students draw the form → POST flow on paper before coding it

---

### Week 8 — Go HTTP Server

**🌐 Online — `net/http` Package**
- `http.HandleFunc`, `http.ListenAndServe`
- `http.ResponseWriter`, `*http.Request`
- Reading form values: `r.FormValue()`
- `r.Method` — checking GET vs POST
- Writing responses: `w.Write`, `w.WriteHeader`
- Live demo: server that echoes back whatever you type in a form

**🏠 Offline — Build the Server**
- Students implement the GET `/` and POST `/ascii-art` endpoints
- Connect the HTML form from last week to the server
- Handle `404` for missing templates and `400` for bad requests
- Test with both browser and `curl`

---

### Week 9 — Go Templates

**🌐 Online — `html/template` Package**
- `template.ParseFiles`, `template.Execute`
- Passing data from Go to HTML: `{{ .Variable }}`
- `{{ if }}`, `{{ range }}`, `{{ with }}` in templates
- Keeping templates in a `templates/` directory
- Live demo: render a list of items from a Go slice in HTML

**🏠 Offline — ascii-art-web Project Completion**
- Integrate Go templates into the server
- Display the ASCII art result on the page after POST
- Add proper error pages (404, 500)
- Write a `README.md` with description, authors, usage, algorithm
- Final demo: each student runs their server and others test it in the browser

---

### Week 10 — Review + Testing Web Handlers

**🌐 Online — Testing in Go**
- `testing` package recap
- `httptest.NewRecorder`, `httptest.NewRequest`
- Testing HTTP handlers without running a server
- Table-driven tests — cleaner test structure
- Live demo: write a test for the POST handler

**🏠 Offline — Test Writing Session**
- Students write tests for their ascii-art-web handlers
- Challenge: write a test that sends `"Hello"` to the POST endpoint and checks the response contains the correct ASCII output
- Peer test swap: run each other's test suites and report what breaks

---

---

# 📅 Month 4 — groupie-tracker
> **Goal:** Consume a real API and display data on a website
> **Teaches:** JSON decoding, HTTP client, structs, client-server events

---

### Week 11 — JSON & Structs

**🌐 Online — Working with JSON in Go**
- `encoding/json` — `json.Unmarshal`, `json.Marshal`
- Defining structs that match JSON shape
- Struct tags: `` `json:"field_name"` ``
- Nested structs and slices of structs
- Live demo: decode the groupie-tracker `/api/artists` response into a Go struct

**🏠 Offline — JSON Challenges**
- Challenge 1: Fetch the artists API and print each artist's name and members
- Challenge 2: Decode the `relation` endpoint (nested map `map[string][]string`)
- Challenge 3: Build a function that finds all locations for a given artist ID
- Students design their data model (structs) for the full project

---

### Week 12 — HTTP Client + Building the Site

**🌐 Online — `http.Get` and API Calls**
- `http.Get(url)` — making requests from Go
- Reading response body: `io.ReadAll`
- Error handling for network calls
- Caching API data in memory to avoid repeated requests
- Structuring a multi-page Go web app

**🏠 Offline — groupie-tracker Build Session**
- Students build the main page showing all artists as cards
- Implement individual artist page (click → detail page)
- Add at least one client-server event (e.g. search/filter that calls the server)
- Discuss: what happens if the API is down?

---

### Week 13 — Events & Client-Server Communication

**🌐 Online — Client-Server Events**
- What is a client-server event vs just page navigation
- Using `fetch` in JavaScript to call a Go endpoint without page reload
- Writing a Go handler that returns JSON
- CORS basics — why browsers block some requests
- Live demo: a search box that filters artists live as you type (JS → Go → JSON response)

**🏠 Offline — groupie-tracker Feature Sprint**
- Students implement their event feature (search, filter by location, sort by year, etc.)
- Facilitator challenge: whose feature is the most creative?
- Add error handling: all pages must work, no crashes
- Unit tests for data fetching and filtering logic

---

### Week 14 — Review + Project Polish

**🌐 Online — Concurrency Basics (Preview)**
- Goroutines — `go func()`
- `sync.WaitGroup` — waiting for goroutines to finish
- Why concurrency matters for web servers (handling multiple requests)
- Live demo: fetch 3 API endpoints concurrently and combine results

**🏠 Offline — groupie-tracker Final Session**
- Students polish their projects: responsive layout, error pages, edge cases
- Each student demos their event feature to the group (2 min each)
- Peer audit: use the project rubric to review a classmate's code
- Introduce lem-in project — first read of the requirements together

---

---

# 📅 Month 5 — lem-in
> **Goal:** Find the optimal path(s) for ants through a graph colony
> **Teaches:** Graph theory, BFS, algorithm design, complex input parsing

---

### Week 15 — Graph Theory Fundamentals

**🌐 Online — Graphs & How to Represent Them**
- What is a graph: nodes (rooms) and edges (tunnels)
- Adjacency list vs adjacency matrix
- Directed vs undirected graphs
- The lem-in problem explained visually
- Live demo: build a graph from the example input file and print its adjacency list

**🏠 Offline — Graph Building Challenges**
- Challenge 1: Parse a lem-in input file and build a `map[string][]string` adjacency list
- Challenge 2: Print all rooms and their direct connections
- Challenge 3: Validate the input — detect missing `##start`, `##end`, duplicate rooms
- Students draw the graph for example 1 on paper before coding

---

### Week 16 — BFS (Breadth-First Search)

**🌐 Online — BFS Algorithm**
- Queue data structure in Go (using a slice)
- BFS step by step — how it finds the shortest path
- Tracking visited nodes to avoid cycles
- Reconstructing the path from end → start using a `parent` map
- Live demo: BFS on the example colony, print the shortest path

**🏠 Offline — BFS Implementation**
- Students implement BFS on their parsed graph
- Challenge 1: find the single shortest path from `##start` to `##end`
- Challenge 2: find ALL shortest paths (same length)
- Challenge 3: handle graph with no path → print `ERROR: invalid data format`
- Debugging session: use `fmt.Println` to trace BFS step by step

---

### Week 17 — Multiple Paths & Ant Movement

**🌐 Online — Optimizing Ant Flow**
- Why one shortest path is not always optimal with many ants
- Finding non-overlapping paths (rooms can't be shared except start/end)
- Deciding how many ants go on each path
- Simulating ant movement turn by turn
- Live demo: walk through example 1 output step by step

**🏠 Offline — Ant Simulation Session**
- Students implement the turn-by-turn ant movement
- Output format: `L1-room L2-room ...` per turn
- Challenge: optimize for minimum number of turns
- Compare outputs: who gets the fewest turns on a complex test case?

---

### Week 18 — Error Handling & Edge Cases

**🌐 Online — Robust Input Parsing**
- Handling comments (`#comment` lines)
- Invalid coordinates, rooms linking to themselves, unknown room links
- Rooms named with numbers vs names
- Returning specific error messages vs generic ones
- Live demo: run 5 edge-case inputs and handle each cleanly

**🏠 Offline — lem-in Project Completion**
- Students finalize lem-in with full error handling
- Test suite: each student brings 3 custom test input files
- Swap test files — does everyone's program handle them correctly?
- Bonus challenge: start the visualizer (print a grid representation of the colony)

---

### Week 19 — Algorithm Review + Complexity

**🌐 Online — Thinking About Performance**
- Big O notation — O(n), O(n²), O(n log n) — just the intuition
- How BFS complexity scales with rooms and tunnels
- When does the lem-in problem become slow? (large graphs)
- Comparing approaches: why your algorithm choices matter
- Introduction to the forum project requirements

**🏠 Offline — lem-in Audit Prep**
- Students prepare to present their lem-in solution to an auditor
- Practice explaining: how does your BFS work? How do you assign ants to paths?
- Pair audits: each student audits one classmate using the official rubric
- Group discussion: what was the hardest part of lem-in?

---

---

# 📅 Month 6 — forum
> **Goal:** Build a full web forum with auth, posts, likes, filtering, and Docker
> **Teaches:** SQL, sessions, cookies, authentication, containerization

---

### Week 20 — Databases & SQL

**🌐 Online — SQLite & SQL Basics**
- What is a relational database? Tables, rows, columns
- `CREATE TABLE`, `INSERT`, `SELECT`, `WHERE`
- Primary keys, foreign keys
- Entity Relationship Diagram (ERD) — designing the forum schema
- Live demo: create a `users` and `posts` table in SQLite and insert/query data

**🏠 Offline — Schema Design Session**
- Students design their ERD: users, posts, comments, categories, likes
- Challenge: write SQL to create all tables with correct relationships
- Challenge: write queries for — get all posts, get posts by user, get likes count
- Set up the `go-sqlite3` driver and run first queries from Go

---

### Week 21 — Authentication & Sessions

**🌐 Online — Auth Fundamentals**
- How registration and login work
- Password hashing with `bcrypt` — never store plain text passwords
- What is a session? What is a cookie?
- Setting and reading cookies in Go (`http.SetCookie`, `r.Cookie`)
- Session expiration — how long should a session last?
- Live demo: register a user, hash their password, store in DB, verify on login

**🏠 Offline — Auth Implementation**
- Students implement registration (email unique check, password hash)
- Implement login (verify password with `bcrypt.CompareHashAndPassword`)
- Set a session cookie on successful login
- Protect routes: only logged-in users can create posts
- Test: try to access protected route without login → redirect to login page

---

### Week 22 — Posts, Comments & Likes

**🌐 Online — CRUD with SQLite in Go**
- `database/sql` package — `db.Query`, `db.QueryRow`, `db.Exec`
- Scanning query results into structs
- Transactions — when multiple queries must succeed together
- Preventing SQL injection — always use `?` placeholders
- Live demo: create a post, retrieve all posts with author name using a JOIN

**🏠 Offline — Forum Core Features**
- Students implement: create post, view all posts, add comment
- Implement likes/dislikes — toggle (like again = remove like)
- Display like/dislike counts to all users (including non-registered)
- Challenge: implement category association when creating a post

---

### Week 23 — Filtering & Docker

**🌐 Online — Docker Basics**
- What is Docker and why it exists
- `Dockerfile` — `FROM`, `RUN`, `COPY`, `EXPOSE`, `CMD`
- `docker build`, `docker run`
- Why containers solve "works on my machine" problems
- Live demo: containerize the ascii-art-web project from Month 3

**🏠 Offline — Forum Filtering + Docker**
- Students implement 3 filters: by category, by created posts, by liked posts
- Write the `Dockerfile` for the forum project
- Build and run the forum inside Docker — test all features still work
- Challenge: filter by multiple categories at once

---

### Week 24 — Final Polish, Testing & Demo Day 🎓

**🌐 Online — Security & Error Handling**
- HTTP error handling: `404`, `400`, `500` — custom error pages
- Input validation — never trust user input
- XSS basics — why you should use `html/template` not `text/template`
- UUID for session tokens — why random IDs are safer than sequential ones
- Review: the full journey from Week 1 to now

**🏠 Offline — Demo Day 🎉**
- Each student demos their forum (5 min each):
  - Register, login, create post with category, like a comment, filter posts
  - Run it inside Docker
- Group vote: most creative UI, most robust error handling, cleanest code
- Retrospective: what was hardest? What clicked? What's next?
- Facilitator: introduce what comes after — microservices, CI/CD, cloud deployment

---

---

## 🗓 Full Calendar Summary

| Week | 🌐 Online Topic | 🏠 Offline Focus | Project |
|------|----------------|-----------------|---------|
| 1 | Functions & Error Handling | Go Gladiators Exercises | go-reloaded |
| 2 | strings & strconv packages | String transformation challenges | go-reloaded |
| 3 | os & bufio packages | go-reloaded project build | go-reloaded |
| 4 | Runes, bytes & ASCII | Banner file parsing | ascii-art |
| 5 | 2D output row by row | ascii-art project build | ascii-art |
| 6 | Good practices & go fmt | Code refactor + peer review | ascii-art |
| 7 | HTTP fundamentals | HTML form building | ascii-art-web |
| 8 | net/http package | Build the server | ascii-art-web |
| 9 | html/template package | Project completion | ascii-art-web |
| 10 | Testing HTTP handlers | Test writing session | ascii-art-web |
| 11 | JSON & structs | JSON decoding challenges | groupie-tracker |
| 12 | HTTP client & API calls | Build artist pages | groupie-tracker |
| 13 | Client-server events | Feature sprint | groupie-tracker |
| 14 | Concurrency basics | Project polish + demo | groupie-tracker |
| 15 | Graph theory & representation | Graph building challenges | lem-in |
| 16 | BFS algorithm | BFS implementation | lem-in |
| 17 | Multi-path & ant movement | Ant simulation | lem-in |
| 18 | Robust input parsing | Project completion | lem-in |
| 19 | Algorithm complexity | Audit prep + peer audits | lem-in |
| 20 | SQLite & SQL basics | Schema design session | forum |
| 21 | Auth & sessions | Auth implementation | forum |
| 22 | CRUD with database/sql | Posts, comments & likes | forum |
| 23 | Docker basics | Filtering + Dockerize | forum |
| 24 | Security & error handling | **Demo Day 🎉** | forum |

---

## 📌 Notes for the Facilitator

- **Online sessions** are concept-first with a live demo — keep them under 1 hour, always end with a concrete takeaway
- **Offline sessions** are hands-on — students should be writing code within the first 10 minutes
- Each project has at least one **peer review or audit** session built in — this mirrors the real audit system they'll face
- The **Go Gladiators** competitive format (Week 1) can be reused at the start of any offline session as a warm-up for 15 minutes
- Projects build on each other: ascii-art → ascii-art-web reuses ascii-art code; forum reuses all HTTP knowledge from Months 3–4
- If a week runs long, the **review weeks** (6, 10, 14, 19) are the safest to compress
