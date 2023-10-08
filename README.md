# codsoft-task 2
import tkinter as tk


class TodoListApp:
    def __init__(self, root):
        self.root = root
        self.root.title("To-Do List BY ANSHIKA ")
      
        self.tasks = []
        
        self.task_entry = tk.Entry(root, width=50)
        self.task_entry.pack(pady=20)
      
        add_button = tk.Button(root, text="Add Task", command=self.add_task)
        add_button.pack()
        self.task_listbox = tk.Listbox(root, width=60, height=20)
        self.task_listbox.pack(pady=20)
        
        remove_button = tk.Button(root, text="Remove Task", command=self.remove_task)
        remove_button.pack()
      
        self.task_listbox.bind("<Double-1>", self.remove_task)
        
    def add_task(self):
        task = self.task_entry.get()
        if task:
            self.tasks.append(task)
            self.update_task_list()
            self.task_entry.delete(0, tk.END) 
    
    def remove_task(self, event=None):
        selected_task_index = self.task_listbox.curselection()
        if selected_task_index:
            index = selected_task_index[0]
            self.tasks.pop(index)
            self.update_task_list()
    
    def update_task_list(self):
        self.task_listbox.delete(0, tk.END)
        for task in self.tasks:
            self.task_listbox.insert(tk.END, task)

if __name__ == "__main__":
    root = tk.Tk()
    app = TodoListApp(root)
    root.mainloop()
