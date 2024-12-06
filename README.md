# CODSOFT
# To-do list
```
def clear_screen():
    """Clears the terminal screen."""
    os.system('cls' if os.name == 'nt' else 'clear')

def display_menu():
    """Displays the main menu."""
    print("\n--- To-Do List Application ---")
    print("1. View To-Do List")
    print("2. Add Task")
    print("3. Update Task")
    print("4. Delete Task")
    print("5. Exit")

def view_tasks(tasks):
    """Displays all tasks."""
    print("\n--- Your To-Do List ---")
    if not tasks:
        print("No tasks available.")
    else:
        for index, task in enumerate(tasks, start=1):
            print(f"{index}. {task}")

def add_task(tasks):
    """Adds a new task."""
    task = input("Enter the task: ")
    if task.strip():
        tasks.append(task)
        print("Task added successfully!")
    else:
        print("Task cannot be empty.")

def update_task(tasks):
    """Updates an existing task."""
    view_tasks(tasks)
    try:
        task_index = int(input("Enter the task number to update: ")) - 1
        if 0 <= task_index < len(tasks):
            new_task = input("Enter the updated task: ")
            if new_task.strip():
                tasks[task_index] = new_task
                print("Task updated successfully!")
            else:
                print("Updated task cannot be empty.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def delete_task(tasks):
    """Deletes a task."""
    view_tasks(tasks)
    try:
        task_index = int(input("Enter the task number to delete: ")) - 1
        if 0 <= task_index < len(tasks):
            deleted_task = tasks.pop(task_index)
            print(f"Task '{deleted_task}' deleted successfully!")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Please enter a valid number.")

def main():
    """Main function to run the To-Do List application."""
    tasks = []
    while True:
        clear_screen()
        display_menu()
        choice = input("\nEnter your choice (1-5): ")
        if choice == '1':
            view_tasks(tasks)
        elif choice == '2':
            add_task(tasks)
        elif choice == '3':
            update_task(tasks)
        elif choice == '4':
            delete_task(tasks)
        elif choice == '5':
            print("Goodbye!")
            break
        else:
            print("Invalid choice. Please try again.")

        input("\nPress Enter to continue...")

if __name__ == "__main__":
    main()
```
# calculator
```
def calculator():
    print("Simple Calculator")
    print("Choose an operation:")
    print("1. Addition (+)")
    print("2. Subtraction (-)")
    print("3. Multiplication (*)")
    print("4. Division (/)")

    
    try:
        num1 = float(input("Enter the first number: "))
        num2 = float(input("Enter the second number: "))
        operation = input("Enter the operation (+, -, *, /): ")

        
        if operation == "+":
            result = num1 + num2
        elif operation == "-":
            result = num1 - num2
        elif operation == "*":
            result = num1 * num2
        elif operation == "/":
            if num2 != 0:
                result = num1 / num2
            else:
                print("Error: Division by zero is not allowed.")
                return
        else:
            print("Invalid operation. Please choose +, -, *, or /.")
            return

        
        print(f"The result of {num1} {operation} {num2} is: {result}")
    except ValueError:
        print("Error: Invalid input. Please enter numeric values.")


calculator()
```
# password
```
import random
import string

def generate_password(length):
    """
    Generate a random password of the specified length.
    
    Parameters:
        length (int): The length of the password to be generated.
        
    Returns:
        str: The generated password.
    """
    if length < 1:
        raise ValueError("Password length must be at least 1")

    
    characters = string.ascii_letters + string.digits + string.punctuation

    
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def main():
    try:
        
        length = int(input("Enter the desired length of the password: "))

        
        password = generate_password(length)
        print(f"Generated Password: {password}")
    except ValueError:
        print("Invalid input. Please enter a positive integer for the password length.")

if __name__ == "__main__":
    main()
```
# rock paper
```
import random

def get_computer_choice():
    return random.choice(["rock", "paper", "scissors"])

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "tie"
    elif (
        (user_choice == "rock" and computer_choice == "scissors") or
        (user_choice == "scissors" and computer_choice == "paper") or
        (user_choice == "paper" and computer_choice == "rock")
    ):
        return "user"
    else:
        return "computer"

def display_result(user_choice, computer_choice, winner):
    print(f"\nYou chose: {user_choice}")
    print(f"Computer chose: {computer_choice}")
    if winner == "tie":
        print("It's a tie!")
    elif winner == "user":
        print("You win!")
    else:
        print("Computer wins!")

def main():
    user_score = 0
    computer_score = 0

    print("Welcome to Rock, Paper, Scissors!")
    print("Type 'exit' anytime to quit the game.\n")

    while True:
        user_choice = input("Choose rock, paper, or scissors: ").lower()
        if user_choice == "exit":
            print("Thanks for playing! Goodbye!")
            break

        if user_choice not in ["rock", "paper", "scissors"]:
            print("Invalid choice. Please choose rock, paper, or scissors.")
            continue

        computer_choice = get_computer_choice()
        winner = determine_winner(user_choice, computer_choice)

        if winner == "user":
            user_score += 1
        elif winner == "computer":
            computer_score += 1

        display_result(user_choice, computer_choice, winner)

        print(f"\nScores: You {user_score} - {computer_score} Computer")
        play_again = input("Do you want to play again? (yes/no): ").lower()
        if play_again != "yes":
            print("Thanks for playing! Final Scores:")
            print(f"You: {user_score} | Computer: {computer_score}")
            break

if __name__ == "__main__":
    main()
```
# contact
```
import tkinter as tk
from tkinter import messagebox

def add_contact():
    name = name_var.get()
    phone = phone_var.get()
    email = email_var.get()
    address = address_var.get()

    if not name or not phone:
        messagebox.showwarning("Input Error", "Name and Phone are required fields.")
        return

    contacts.append({"name": name, "phone": phone, "email": email, "address": address})
    messagebox.showinfo("Success", "Contact added successfully!")
    clear_inputs()
    display_contacts()

def clear_inputs():
    name_var.set("")
    phone_var.set("")
    email_var.set("")
    address_var.set("")

def display_contacts():
    contact_list.delete(0, tk.END)
    for contact in contacts:
        contact_list.insert(tk.END, f"{contact['name']} - {contact['phone']}")

def search_contact():
    query = search_var.get().lower()
    contact_list.delete(0, tk.END)
    for contact in contacts:
        if query in contact['name'].lower() or query in contact['phone']:
            contact_list.insert(tk.END, f"{contact['name']} - {contact['phone']}")

def delete_contact():
    selected = contact_list.curselection()
    if not selected:
        messagebox.showwarning("Selection Error", "No contact selected.")
        return

    index = selected[0]
    del contacts[index]
    messagebox.showinfo("Success", "Contact deleted successfully!")
    display_contacts()

def update_contact():
    selected = contact_list.curselection()
    if not selected:
        messagebox.showwarning("Selection Error", "No contact selected.")
        return

    index = selected[0]
    contact = contacts[index]
    
    name_var.set(contact['name'])
    phone_var.set(contact['phone'])
    email_var.set(contact['email'])
    address_var.set(contact['address'])

    def save_update():
        contact['name'] = name_var.get()
        contact['phone'] = phone_var.get()
        contact['email'] = email_var.get()
        contact['address'] = address_var.get()

        messagebox.showinfo("Success", "Contact updated successfully!")
        clear_inputs()
        display_contacts()
        save_btn.pack_forget()

    save_btn.pack(pady=5)


root = tk.Tk()
root.title("Contact Manager")


contacts = []
name_var = tk.StringVar()
phone_var = tk.StringVar()
email_var = tk.StringVar()
address_var = tk.StringVar()
search_var = tk.StringVar()


frame = tk.Frame(root)
frame.pack(padx=10, pady=10)

tk.Label(frame, text="Name:").grid(row=0, column=0, sticky=tk.W)
tk.Entry(frame, textvariable=name_var).grid(row=0, column=1, padx=5, pady=5)

tk.Label(frame, text="Phone:").grid(row=1, column=0, sticky=tk.W)
tk.Entry(frame, textvariable=phone_var).grid(row=1, column=1, padx=5, pady=5)

tk.Label(frame, text="Email:").grid(row=2, column=0, sticky=tk.W)
tk.Entry(frame, textvariable=email_var).grid(row=2, column=1, padx=5, pady=5)

tk.Label(frame, text="Address:").grid(row=3, column=0, sticky=tk.W)
tk.Entry(frame, textvariable=address_var).grid(row=3, column=1, padx=5, pady=5)


btn_frame = tk.Frame(frame)
btn_frame.grid(row=4, column=0, columnspan=2, pady=10)

tk.Button(btn_frame, text="Add Contact", command=add_contact).grid(row=0, column=0, padx=5)
tk.Button(btn_frame, text="Search", command=search_contact).grid(row=0, column=1, padx=5)
tk.Button(btn_frame, text="Update Contact", command=update_contact).grid(row=0, column=2, padx=5)
tk.Button(btn_frame, text="Delete Contact", command=delete_contact).grid(row=0, column=3, padx=5)

save_btn = tk.Button(btn_frame, text="Save Update", command=None)


tk.Label(frame, text="Search:").grid(row=5, column=0, sticky=tk.W)
tk.Entry(frame, textvariable=search_var).grid(row=5, column=1, padx=5, pady=5)
contact_list = tk.Listbox(root, width=50, height=15)
contact_list.pack(padx=10, pady=10)


root.mainloop()
```
