# Lab4

import json

# 1. Load existing tasks from JSON file
def load_tasks(filename="todo.json"):
    try:
        with open(filename, "r") as file:
            data = json.load(file)
            return data["tasks"]
    except (FileNotFoundError, json.JSONDecodeError):
        return []

# 2. Save updated task list back to the JSON file
def save_tasks(tasks, filename="todo.json"):
    with open(filename, "w") as file:
        json.dump({"tasks": tasks}, file, indent=4)

# 3. Main program
def main():
    tasks = load_tasks()
    print("Current tasks:", tasks)

    new_task = input("Add a new task: ")
    tasks.append(new_task)

    save_tasks(tasks)
    print("Task added and saved successfully!")

if __name__ == "__main__":
    main()
