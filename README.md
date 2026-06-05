# LRU Cache in C

An implementation of the **Least Recently Used (LRU)** cache replacement policy in C, built from scratch using a doubly linked list and binary search trees. The program simulates cache requests for application names, tracks hits and misses, and evicts the least recently used entry when the cache is full.

## What is LRU?

LRU (Least Recently Used) is a caching strategy that evicts the least recently accessed item when the cache reaches capacity. Every access marks an item as most recently used, keeping frequently used data readily available. It's widely used in databases, web servers, and file systems to improve performance.

## How It Works

1. When an application is accessed, the program checks whether it's already in the cache (via the BST lookup).
2. If it's **not** in the cache, it's added to both the linked list and the BST — a **cache miss**.
3. If it **is** in the cache, it's moved to the head of the linked list — a **cache hit**.
4. When the cache exceeds its maximum size, the least recently used entry (the tail of the linked list) is removed from both the linked list and the BST.

## Data Structures

The implementation combines three structures:

### Doubly Linked List
Maintains access order, with the most recently used item at the head and the least recently used at the tail.
- `insertList` — insert a new node at the head
- `deleteLastList` — remove the last (least recently used) node
- `print` — display the current cache contents

### Binary Search Tree (Cache Index)
Maps each application name to its node address in the linked list, enabling fast lookups.
- `insertBST` — insert a node with name and linked-list address
- `deleteBST` — delete a node by name
- `searchBST` — search for a node by name
- `heightBST` — compute the tree height
- `pred` / `succ` — find predecessor / successor nodes for deletion

### Usage Record BST
Tracks per-application usage statistics.
- `insertRecord` — add a new application record and initialize hits/misses
- `searchRecord` — look up an application's record
- `Record_print` — print the summary of hits and misses

## Features

- Fixed-size cache (default capacity: 5, set via the `cacheSize` macro)
- O(log n) lookups through the BST index
- Per-application hit/miss statistics
- Interactive menu-driven simulation

## Menu Options

The program runs an interactive loop where you can:
- Access an application (simulate a cache request)
- Display the current cache blocks
- View the usage summary (hits and misses)
- Exit

## Getting Started

### Prerequisites

- A C compiler (e.g., GCC)

### Build and Run

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
gcc lru.c -o lru
./lru
```

> Adjust the cache capacity by editing the `#define cacheSize 5` macro in the source file.

## Author

**Markand Joshi** — Electronics & Communication Department, Nirma University

## License

This project is released under the MIT License. See the `LICENSE` file for details.
