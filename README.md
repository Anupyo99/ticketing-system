# 🎫 Simple Ticketing System (Python CLI)

This is a lightweight **Command Line Interface (CLI) Ticketing System** built in Python. It simulates a basic helpdesk system that allows you to create, view, and update support tickets — all stored in a CSV file.

> 🔧 Great for showcasing beginner Python skills in file handling, user input, and basic data manipulation.

---

## 🚀 Features

- ✅ Create support tickets with timestamped IDs
- ✅ View all open/resolved tickets
- ✅ Update ticket status (e.g., In Progress, Resolved)
- ✅ Store data persistently using CSV (no database needed)
- ✅ Auto-generates the file if it doesn't exist

---

## 📂 Files Included

| File         | Description                           |
|--------------|---------------------------------------|
| `tickets.csv`| Stores ticket data in tabular format  |
| `your_script.py` | Main script to run the ticketing system |

> Replace `your_script.py` with your actual filename.

---

## 🛠 How It Works

When you run the script, you'll get a simple menu with options to:
- **Create Ticket** → Prompts for user name, issue, priority  
- **View Tickets** → Displays all tickets in a readable format  
- **Update Ticket** → Allows status change by ticket ID  
- **Exit** → Quit the application

---

## 📋 Example Ticket Data (CSV)

```csv
Ticket ID,Name,Issue,Priority,Status,Created At
1720288227,Alice,Printer not working,High,Open,2025-07-06 15:40:27
