# Expense Tracker CLI Application (Golang)

## Overview

This project is a **command-line expense tracker application** written in **Go**.  
The application allows users to manage personal expenses by adding, updating, deleting, and viewing expense records. It also provides summaries of expenses overall and by month.

The goal of this task is to assess:
- Command-line application design
- File-based data persistence
- Data modeling and validation
- Clean code structure and error handling in Go

---

## Candidate Instructions

### How to Submit Your Solution

1. **Fork this repository** to your own GitHub account.
2. Implement the solution in your forked repository.
3. Commit your changes with clear and meaningful commit messages.
4. **Create a Pull Request (PR)** from your fork back into this repository.
5. In the Pull Request description, include:
   - Brief explanation of your approach
   - Any assumptions made
   - List of implemented bonus features (if any)
   - Instructions to build and run the application

> ⚠️ **Do not push directly to this repository. Only Pull Requests will be reviewed.**

---

## Functional Requirements

### 1. Add an Expense

Add a new expense with a description and amount.

```bash
$ expense-tracker add --description "Lunch" --amount 20
# Expense added successfully (ID: 1)
```

**Rules**
- Amount must be a positive number
- Description cannot be empty
- Date should default to the current date

---

### 2. Update an Expense

Update an existing expense by ID.

```bash
$ expense-tracker update --id 1 --description "Lunch with client" --amount 25
# Expense updated successfully
```

**Rules**
- Expense ID must exist
- Amount must be a positive number

---

### 3. Delete an Expense

Delete an expense by ID.

```bash
$ expense-tracker delete --id 2
# Expense deleted successfully
```

**Rules**
- Expense ID must exist

---

### 4. List All Expenses

Display all recorded expenses.

```bash
$ expense-tracker list
# ID  Date        Description        Amount
# 1   2024-08-06  Lunch              $20
# 2   2024-08-06  Dinner             $10
```

---

### 5. View Total Expense Summary

Show the total of all expenses.

```bash
$ expense-tracker summary
# Total expenses: $30
```

---

### 6. View Monthly Expense Summary (Current Year)

Show total expenses for a specific month of the current year.

```bash
$ expense-tracker summary --month 8
# Total expenses for August: $20
```

**Rules**
- Month must be between 1 and 12
- Year is assumed to be the current year

---

## Optional (Bonus) Features

These features are optional and not required for completion:

- Expense categories (e.g. Food, Transport, Utilities)
- Filter expenses by category
- Monthly budget settings with warnings when exceeded
- Export expenses to a CSV file

---

## Data Storage

- Expenses must be stored in a **local file**
- Allowed formats:
  - JSON (recommended)
  - CSV
- Data must persist between application runs

### Example Expense Structure (JSON)

```json
{
  "id": 1,
  "description": "Lunch",
  "amount": 20,
  "date": "2024-08-06",
  "category": "Food"
}
```

---

## Technical Requirements

- Language: **Go (Golang)**
- CLI argument parsing:
  - Standard library `flag`
  - OR third-party libraries (e.g. `cobra`)

---

## Error Handling

The application should handle the following cases gracefully:
- Invalid or missing arguments
- Negative or zero amounts
- Non-existent expense IDs
- Invalid month values
- Missing or corrupted data files

Error messages should be clear and user-friendly.

---

## Suggested Project Structure

```
expense-tracker/
├── main.go
├── cmd/
│   ├── add.go
│   ├── update.go
│   ├── delete.go
│   ├── list.go
│   └── summary.go
├── internal/
│   ├── model/
│   │   └── expense.go
│   ├── storage/
│   │   └── file.go
│   └── service/
│       └── expense_service.go
├── data/
│   └── expenses.json
└── README.md
```

*(Project structure is flexible; clarity and maintainability matter more than strict layout.)*

---

## Evaluation Criteria

Candidates will be evaluated based on:
- Code quality and readability
- Proper use of Go idioms
- Error handling and validation
- Data persistence approach
- Maintainability and structure
- Bonus features (if implemented)

---

## Notes for Candidates

- Focus on correctness and clarity
- Avoid over-engineering
- Unit tests are optional but appreciated
- External dependencies should be justified
