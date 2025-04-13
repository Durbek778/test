# Advanced Database Organization  
## Programming Assignment IV: Index Manager – B+ Tree Implementation

### 👨‍💻 Contributors

| CWID       | Name              | Contribution Description                                                                 | % Contribution |
|------------|-------------------|------------------------------------------------------------------------------------------|----------------|
| A20594489  | Kori Kamoljonov   | Designed and implemented the B+ Tree insert, search, delete, and scan operations. Integrated buffer pool. | 33.3%          |
| A20568393  | Chaitanya Datta   | Developed B+ Tree scan sorting and expression evaluation. Assisted with testing and edge case handling. | 33.3%          |
| A20582646  | Vamshi Krishna    | Worked on buffer management, test case development, and tree metadata handling and storage integration. | 33.3%          |

---

## 📌 Project Overview

This assignment focuses on building an **Index Manager** using a **B+ Tree** data structure. It supports standard operations such as **insertion**, **deletion**, **search**, and **scan** on **integer-based keys**, with integration to previously implemented **buffer** and **storage managers**.

Each integer key is uniquely mapped to a **Record ID (RID)**. The implementation prioritizes correctness and modular integration with the larger database system.

---

## ⚙️ Key Features

- Integer key support only.
- Static, unbalanced B+ Tree (no dynamic balancing or node splitting).
- Duplicate key insertions return errors.
- Persistent storage via page files and buffer manager.
- Supports sorted traversal using scan functionality.
- Expression evaluation using custom expression trees.

---

## 🧱 Project Structure


---

## 🔑 Major Components

### 1. `btree_mgr.h`

Defines the core API of the B+ Tree Index Manager:
- **Initialization:** `initIndexManager()`, `shutdownIndexManager()`
- **Metadata Management:** `createBtree()`, `openBtree()`, `closeBtree()`, `deleteBtree()`
- **Key Operations:** `insertKey()`, `findKey()`, `deleteKey()`
- **Scan Operations:** `openTreeScan()`, `nextEntry()`, `closeTreeScan()`
- **Utilities:** `printTree()`, `getNumNodes()`, `getNumEntries()`

> Note: Node splitting and balancing are not implemented. The tree grows as a flat, linked structure.

---

### 2. `expr.h`

Defines the **expression evaluation** system used in scans:
- **Types:** Constants, Attribute References (partially used), Operators
- **Operators:** Comparison (`==`, `<`, etc.), Logical (`AND`, `OR`, `NOT`)
- **Function:** `evalExpr()` evaluates conditions during scans

---

### 3. `tables.h`

Reused from the Record Manager to define:
- **Value** (only `DT_INT` used here)
- **RID** (page + slot)
- **Schema and Record** (minimally used for evaluation compatibility)

---

## 🧪 Test Cases

### `test_expr.c` – Expression Tests
- Integer/string comparison
- Boolean logic: `AND`, `OR`, `NOT`
- Nested expression evaluation
- Edge case handling for types

### `test_assign4_1.c` – Index Tests
- **Insert & Find:** Verifies RID retrieval and node/entry count
- **Delete:** Ensures deleted entries are excluded
- **Scan:** Sorted traversal validation with random order insertions
- Uses assertions: `ASSERT_EQUALS_RID()` and `ASSERT_EQUALS_INT()` for accuracy

---

## 🚫 Features Not Implemented (Future Work)

- Node splitting & dynamic balancing  
- Null value support  
- Primary key enforcement  
- Tombstone records / transaction tracking  
- External sorting for large datasets  
- Interactive CLI or update-based scans  

---

## 🔧 Build & Run

To compile the project, simply run:

```bash
make
