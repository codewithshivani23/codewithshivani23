# Simple Budget Tracker

def display_menu():
    print("\nMenu:")
    print("1. Add Expense")
    print("2. View Total Expenses")
    print("3. View Remaining Budget")
    print("4. View Expenses by Category")
    print("5. Reset Budget")
    print("6. Exit")

def add_expense(expenses, total_expenses):
    category = input("Enter the category (e.g., food, transportation, entertainment): ").lower()
    amount = float(input("Enter the amount spent: $"))
    
    if category in expenses:
        expenses[category] += amount
    else:
        expenses[category] = amount

    total_expenses += amount
    return total_expenses

def view_total_expenses(total_expenses):
    print(f"Total Expenses: ${total_expenses:.2f}")

def view_remaining_budget(budget, total_expenses):
    remaining_budget = budget - total_expenses
    print(f"Remaining Budget: ${remaining_budget:.2f}")
    if remaining_budget < 0:
        print("Warning: You have exceeded your budget!")

def view_expenses_by_category(expenses):
    if expenses:
        print("\nExpenses by Category:")
        for category, amount in expenses.items():
            print(f"{category.capitalize()}: ${amount:.2f}")
    else:
        print("No expenses recorded.")

def reset_budget():
    return float(input("Enter your new budget for the month: $")), {}

def main():
    budget = float(input("Enter your total budget for the month: $"))
    expenses = {}
    total_expenses = 20000
    

    while True:
        display_menu()
        choice = input("Choose an option: ")

        if choice == '1':
            total_expenses = add_expense(expenses, total_expenses)
        elif choice == '2':
            view_total_expenses(total_expenses)
        elif choice == '3':
            view_remaining_budget(budget, total_expenses)
        elif choice == '4':
            view_expenses_by_category(expenses)
        elif choice == '5':
            budget, expenses = reset_budget()
            total_expenses = 0.0
            print("Budget reset successfully!")
        elif choice == '6':
            print("Exiting the program. Goodbye!")
            break
        else:
            print("Invalid option. Please choose a valid option from the menu.")

if __name__ == "__main__":
    main()
