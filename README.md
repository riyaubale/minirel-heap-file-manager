# Minirel Heap File Manager – Database Systems Project

A C++ implementation of a Heap File Manager for the Minirel database system, supporting logical file organization, record insertion/deletion, and filtered record scanning.

---

## Project Overview

This project extends the Minirel DBMS by implementing a logical heap file layer on top of the physical storage layer. The heap file manager organizes database pages using linked lists and provides efficient mechanisms for:
- Record insertion
- Record deletion
- Sequential scanning
- Predicate-based filtering

The system integrates closely with the Minirel buffer manager and storage layer.

---

## Features

- Implemented logical heap file organization using linked pages
- Built heap file creation and destruction functionality
- Added support for:
  - Record insertion
  - Record retrieval
  - Record deletion
  - Sequential scans
  - Predicate filtering
- Implemented scan bookmarking and reset functionality
- Managed pinned pages through the buffer manager
- Integrated record-level operations with page-level storage

---

## Core Components

### `FileHdrPage`
Stores metadata for each heap file:
- File name
- First data page
- Last data page
- Total page count
- Total record count

### `HeapFile`
Provides core heap file operations:
- Open/close heap files
- Retrieve records by RID
- Track current pinned pages
- Manage file metadata

### `HeapFileScan`
Extends `HeapFile` to support:
- Sequential scans
- Predicate filtering
- Record deletion during scans
- Scan bookmarking and resetting

### `InsertFileScan`
Supports efficient record insertion into heap files.

---

## Key Functionalities

### Heap File Creation
Implemented:
- `createHeapFile()`
- `destroyHeapFile()`

Features:
- Initializes file header page
- Creates first linked data page
- Updates file metadata
- Integrates with buffer manager page allocation

---

## Scan Mechanism

Implemented filtered scanning using:
- Integer attributes
- Float attributes
- String attributes
- Comparison operators

Supported operations:
- Equality
- Inequality
- Greater/Less than comparisons

The scan system efficiently traverses linked data pages while keeping pages pinned only when needed.

---

## Record Operations

### Insert Records
- Inserts records into available pages
- Allocates new pages when full
- Updates linked list structure
- Maintains record counts

### Retrieve Records
- Retrieves records using RIDs
- Uses pinned page tracking for efficiency

### Delete Records
- Removes records directly from pages
- Supports deletion during scans

---

## Technologies Used

- C++
- Object-Oriented Programming
- Database Storage Systems
- Heap File Organization
- Buffer Management
- Record Management

---

## Project Structure

```text
.
├── heapfile.h        # Heap file class definitions
├── heapfile.C        # Heap file implementation
├── buf.h             # Buffer manager definitions
├── buf.C             # Buffer manager implementation
├── db.h              # I/O layer definitions
├── db.C              # I/O layer implementation
├── page.h            # Page class definitions
├── page.C            # Page implementation
├── error.h           # Error definitions
├── error.C           # Error handling
├── testfile.C        # Heap file test driver
└── Makefile          # Build configuration
