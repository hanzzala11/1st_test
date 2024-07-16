# Submitted by : Hanzzala Siddique 
# Institute : IUB pakistan
# Email : hanzzalas@gmail.com
# Submitted to: Dr.Geroge Wlliem

## Code:
import tkinter as tk

'''
 Create the main window
 '''
 
root = tk.Tk()
root.title("Simple Calculator")

''' Entry widget to display the input and result
'''

entry = tk.Entry(root, width=16, font=('Arial', 24), borderwidth=2, relief="solid")
entry.grid(row=0, column=0, columnspan=4)

'''
Define button click function
'''

def button_click(number):
    current = entry.get()
    entry.delete(0, tk.END)
    entry.insert(0, current + str(number))

'''
 Define button clear function
 '''

def button_clear():
    entry.delete(0, tk.END)

'''
Define button equal function
'''

def button_equal():
    try:
        result = str(eval(entry.get()))
        entry.delete(0, tk.END)
        entry.insert(0, result)
    except:
        entry.delete(0, tk.END)
        entry.insert(0, "Error")

'''
 Define button creation function
 '''

def create_button(text, row, column, command):
    button = tk.Button(root, text=text, padx=20, pady=20, font=('Arial', 18), command=command)
    button.grid(row=row, column=column, sticky="nsew")

'''
 Define buttons
 '''

buttons = [
    ('7', 1, 0), ('8', 1, 1), ('9', 1, 2), ('/', 1, 3),
    ('4', 2, 0), ('5', 2, 1), ('6', 2, 2), ('*', 2, 3),
    ('1', 3, 0), ('2', 3, 1), ('3', 3, 2), ('-', 3, 3),
    ('0', 4, 0), ('.', 4, 1), ('+', 4, 2), ('=', 4, 3)
]

'''
 Add buttons to the grid
 '''

for (text, row, column) in buttons:
    if text == '=':
        create_button(text, row, column, button_equal)
    else:
        create_button(text, row, column, lambda text=text: button_click(text))

'''
 Add clear button
 '''

create_button("C", 5, 0, button_clear)

'''
Run the main loop
'''
root.mainloop()

## Output: