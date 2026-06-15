### Test
The test I use is:
> "If Docker disappeared tomorrow, would this knowledge still be useful?"
If yes, it's probably a Concept.
Examples:
- DNS → Concept
- HTTP → Concept
- Mutex → Concept
- REST → Concept
- ACID → Concept
- Caching → Concept
If no, it's probably a Tool.
Examples:
- Docker Compose commands → Tool
- GitHub Actions syntax → Tool
- Vim keybindings → Tool
- systemctl commands → Tool
### How I would organize it
I would separate knowledge into four categories:
```
IT/  
├── Concepts/  
├── Languages/  
├── Tools/  
├── Projects/  
└── Cheatsheets/
```
### Languages
Language-specific syntax and idioms.
```
Languages/
├── Go/
│   ├── Goroutines
│   ├── Interfaces
│   └── Error Handling
├── Python/
└── C#
└── SQL/
```
If a note only makes sense in Go, it belongs here.
### Tools
Actual software you use.
```
Tools/  
├── Linux/  
├── Git/  
├── Docker/  
├── Kubernetes/  
├── Vim/  
├── Obsidian/  
└── PostgreSQL/
```
Docker is a tool. Vim is a tool. Git is a tool.

### Concepts
Fundamental concepts that exist regardless of language or tool
```
Concepts/  
├── Algorithms/  
│ ├── Binary Search  
│ ├── BFS  
│ ├── DFS  
│ ├── Dynamic Programming  
│ └── Dijkstra  
│  
├── Data Structures/  
│ ├── Array  
│ ├── Linked List  
│ ├── Hash Table  
│ ├── Heap  
│ └── Trie
|
├── Concurrency/  
│ ├── Mutex  
│ ├── Semaphore  
│ ├── Deadlock  
│ ├── Race Condition  
│ └── Thread Safety  
│  
├── Networking/
│   ├── DNS
│   ├── HTTP
│   ├── TCP
│   ├── UDP
│   ├── TLS
│   ├── REST
│   ├── WebSockets
│   └── gRPC
|
├── Memory/  
│ ├── Heap  
│ ├── Stack  
│ ├── Virtual Memory  
│ ├── Garbage Collection  
│ ├── Memory Leak  
│ └── Reference Counting  
│  
├── Programming/  
│ ├── Closure  
│ ├── Polymorphism  
│ ├── Inheritance  
│ ├── Composition  
│ ├── Reflection  
│ └── Generics  
│  
├── Data Representation/  
│ ├── Little Endian  
│ ├── Big Endian  
│ ├── UTF-8  
│ └── Binary Encoding  
│  
└── Performance/  
|   ├── Memoization  
|   ├── Caching  
|   └── Complexity Analysis
|
├── Data Formats/
│   ├── JSON
│   ├── XML
│   ├── YAML
│   └── CSV
|
├── Databases/
│   ├── Indexes
│   ├── Transactions
│   ├── Normalization
│   └── CAP Theorem
|
├── Operating Systems/  
|
├── Security/  
|
├── Architecture/  
    ├── API Design  
    ├── Authentication  
    ├── Authorization  
    ├── Load Balancing  
    ├── Caching Strategies  
    ├── Message Queues  
    ├── Event Driven Architecture  
    ├── Microservices  
    ├── Monoliths  
    ├── CQRS  
    ├── Event Sourcing  
    └── Observability
```