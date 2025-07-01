import csv
import os
import datetime

TICKET_FILE = "tickets.csv"
FIELDS = ["Ticket ID", "Name", "Issue", "Priority", "Status", "Created At"]

# Initialize CSV if it doesn't exist
def initialize_file():
    if not os.path.exists(TICKET_FILE):
        with open(TICKET_FILE, mode="w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(FIELDS)
R
# Create a new ticket
def create_ticket():
    name = input("Enter user's name: ")
    issue = input("Describe the issue: ")
    priority = input("Priority (Low/Medium/High): ").capitalize()

    ticket_id = str(int(datetime.datetime.now().timestamp()))
    status = "Open"
    created_at = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

    with open(TICKET_FILE, mode="a", newline="") as file:
        writer = csv.writer(file)
        writer.writerow([ticket_id, name, issue, priority, status, created_at])

    print(f"✅ Ticket created with ID: {ticket_id}\n")

# View all tickets
def view_tickets():
    with open(TICKET_FILE, mode="r") as file:
        reader = csv.reader(file)
        next(reader)  # skip header
        print("\n📋 All Tickets:\n")
        for row in reader:
            print(f"ID: {row[0]}, User: {row[1]}, Issue: {row[2]}, Priority: {row[3]}, Status: {row[4]}, Created: {row[5]}")
    print("")

# Update a ticket
def update_ticket():
    ticket_id = input("Enter Ticket ID to update: ")
    updated = False

    rows = []
    with open(TICKET_FILE, mode="r") as file:
        reader = csv.reader(file)
        header = next(reader)
        for row in reader:
            if row[0] == ticket_id:
                print(f"Current status: {row[4]}")
                new_status = input("Update status to (In Progress / Resolved): ").title()
                row[4] = new_status
                updated = True
            rows.append(row)

    if updated:
        with open(TICKET_FILE, mode="w", newline="") as file:
            writer = csv.writer(file)
            writer.writerow(header)
            writer.writerows(rows)
        print("✅ Ticket updated.\n")
    else:
        print("❌ Ticket ID not found.\n")

# Main menu
def menu():
    initialize_file()
    while True:
        print("🎫 Ticketing System Menu:")
        print("1. Create Ticket")
        print("2. View All Tickets")
        print("3. Update Ticket Status")
        print("4. Exit")

        choice = input("Select an option (1–4): ")
        if choice == "1":
            create_ticket()
        elif choice == "2":
            view_tickets()
        elif choice == "3":
            update_ticket()
        elif choice == "4":
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Try again.\n")

if __name__ == "__main__":
    menu()
