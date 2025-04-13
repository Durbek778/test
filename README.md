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

