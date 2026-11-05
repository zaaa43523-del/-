# -import tkinter as tk

def on_click(button_text):
    if button_text == "=":
        try:
            result = eval(entry.get())
            entry.delete(0, tk.END)
            entry.insert(tk.END, str(result))
        except Exception as e:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    else:
        entry.insert(tk.END, button_text)

root = tk.Tk()
root.title("آلة حاسبة حديثة")

entry = tk.Entry(root, width=20, font=('Arial', 24), borderwidth=2, relief='ridge')
entry.grid(row=0, column=0, columnspan=4)

buttons = [
    ('7', '8', '9', '/'),
    ('4', '5', '6', '*'),
    ('1', '2', '3', '-'),
    ('0', '.', '=', '+')
]

for i, row in enumerate(buttons):
    for j, button_text in enumerate(row):
        btn = tk.Button(root, text=button_text, width=5, height=2, font=('Arial', 18), command=lambda t=button_text: on_click(t))
        btn.grid(row=i+1, column=j)

root.mainloop()