# task_tracker.py

class Task:
    def __init__(self, description, due_date):
        self.description = description
        self.due_date = due_date
        self.completed = False

class TaskTracker:
    def __init__(self):
        self.tasks = []

    def add_task(self, description, due_date):
        task = Task(description, due_date)
        self.tasks.append(task)
        print(f"Task '{description}' added successfully!")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks found.")
        else:
            for index, task in enumerate(self.tasks, start=1):
                print(f"{index}. {task.description} (Due: {task.due_date}) - {'Completed' if task.completed else 'Pending'}")

    def mark_task_completed(self, task_index):
        if 1 <= task_index <= len(self.tasks):
            task = self.tasks[task_index - 1]
            task.completed = True
            print(f"Task '{task.description}' marked as completed!")
        else:
            print("Invalid task index.")

    def view_completed_tasks(self):
        completed_tasks = [task for task in self.tasks if task.completed]
        if not completed_tasks:
            print("No completed tasks found.")
        else:
            for index, task in enumerate(completed_tasks, start=1):
                print(f"{index}. {task.description} (Due: {task.due_date})")

if __name__ == "__main__":
    tracker = TaskTracker()

    while True:
        print("\nTask Tracker Menu:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Mark Task as Completed")
        print("4. View Completed Tasks")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            description = input("Enter task description: ")
            due_date = input("Enter due date (YYYY-MM-DD): ")
            tracker.add_task(description, due_date)

        elif choice == '2':
            print("\nAll Tasks:")
            tracker.view_tasks()

        elif choice == '3':
            task_index = int(input("Enter the index of the task to mark as completed: "))
            tracker.mark_task_completed(task_index)

        elif choice == '4':
            print("\nCompleted Tasks:")
            tracker.view_completed_tasks()

        elif choice == '5':
            print("Exiting Task Tracker. Goodbye!")
            break

        else:
            print("Invalid choice. Please try again.")
