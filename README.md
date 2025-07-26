# codsoft_1
GUI Calculator
import tkinter as tk

def click(event):
    text = event.widget.cget("text")
    if text == "=":
        try:
            result = eval(str(entry.get()))
            entry.delete(0, tk.END)
            entry.insert(tk.END, result)
        except Exception:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif text == "C":
        entry.delete(0, tk.END)
    else:
        entry.insert(tk.END, text)

root = tk.Tk()
root.title("Responsive Calculator")

root.rowconfigure(1, weight=1)
root.columnconfigure(0, weight=1)

entry = tk.Entry(root, font="Arial 20", justify="right")
entry.grid(row=0, column=0, sticky="nsew", padx=10, pady=10)

button_frame = tk.Frame(root)
button_frame.grid(row=1, column=0, sticky="nsew")

for i in range(5):  # 5 rows
    button_frame.rowconfigure(i, weight=1)
for j in range(4):  # 4 columns
    button_frame.columnconfigure(j, weight=1)

buttons = [
    ["7", "8", "9", "/"],
    ["4", "5", "6", "*"],
    ["1", "2", "3", "-"],
    ["0", ".", "C", "+"],
    ["="]
]

for i, row in enumerate(buttons):
    for j, btn_text in enumerate(row):
        button = tk.Button(button_frame, text=btn_text, font="Arial 18", relief="ridge")
        button.grid(row=i, column=j, sticky="nsew")
        button.bind("<Button-1>", click)

root.mainloop()
