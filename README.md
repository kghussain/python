#python_cal
import tkinter as tk

def button_click(number):
    current = entry_box.get()
    entry_box.delete(0, tk.END)
    entry_box.insert(0, current + str(number))

def button_clear():
    entry_box.delete(0, tk.END)

def button_equal():
    try:
        result = eval(entry_box.get())
        entry_box.delete(0, tk.END)
        entry_box.insert(0, result)
    except:
        entry_box.delete(0, tk.END)
        entry_box.insert(0, "Error")

# Create the main window
root = tk.Tk()
root.title("Calculator")

# Create entry box
entry_box = tk.Entry(root, width=35, borderwidth=5)
entry_box.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Define buttons
buttons = [
    ("7", 1, 0), ("8", 1, 1), ("9", 1, 2), ("*", 1, 3),
    ("4", 2, 0), ("5", 2, 1), ("6", 2, 2), ("/", 2, 3),
    ("1", 3, 0), ("2", 3, 1), ("3", 3, 2), ("+", 3, 3),
    ("0", 4, 0), (".", 4, 1), ("=", 4, 2), ("-", 4, 3),
]

# Create buttons
for (text, row, column) in buttons:
    button = tk.Button(root, text=text, padx=30, pady=20, command=lambda t=text: button_click(t))
    button.grid(row=row, column=column)

# Clear button
clear_button = tk.Button(root, text="Clear", padx=24, pady=20, command=button_clear)
clear_button.grid(row=5, column=0, columnspan=2)

# Equal button
equal_button = tk.Button(root, text="=", padx=65, pady=20, command=button_equal)
equal_button.grid(row=5, column=2, columnspan=2)

root.mainloop()
