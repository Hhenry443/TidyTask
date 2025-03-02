
# Tidy Task
This script provides a command-line interface (CLI) for managing tasks. You can add, view, edit, mark as done, delete, and clear tasks. All tasks are stored in a `tasks.json` file, located in the specified path. You will need to change this in the script!!

## Requirements
-   Python 3.x
-   The  `argparse`  and  `json`  libraries (both come with Python by default).
## Features
1.   **Add a task**  
		    - Add a new task with a description.
    
2.   **View tasks**  
		    - View all tasks or a specific task by its ID. Marked tasks are displayed with a strikethrough.
    
3.    **Edit a task**  
		    - Edit the description of an existing task.
    
4.    **Mark a task as done**  
		    - Mark a task as completed (or mark it as incomplete).
    
5.  **Delete a task**  
	    - Delete a task by its ID and reassign task IDs.
    
6.    **Clear all tasks** 
			- Delete all tasks in the planner.
## Setup
### Step One: Clone the Repository
Clone the repository to your local machine using Git:
`git clone https://github.com/Hhenry443/TidyTask.git` 
### Step Two: Make the Script Executable
You need to give the  `planner` file permission to be executed as a script.

Run this command in your terminal:
`chmod +x /path/to/TidyTask/planner` 

Make sure to replace  `/path/to/TidyTask`  with the actual path where you've cloned the repository.

### Step Three: Add the Directory to Your PATH
To make the script easily accessible from anywhere, add the directory containing the script to your system's  `PATH`. This way, you can run it without needing to navigate to the directory where the script is located.

Run the following command in your terminal:
`echo 'export PATH="/path/to/TidyTask:$PATH"' >> ~/.bashrc` 

For users with  `zsh`  (the default shell for macOS), use this instead:
`echo 'export PATH="/path/to/TidyTask:$PATH"' >> ~/.zshrc` 

Afterwards, apply the changes by running:
`source ~/.bashrc  # For bash users`

`source ~/.zshrc   # For zsh users`
### Step Four: Run it as a Command
Now, you can run the script by typing:
`planner` 

from anywhere in the terminal, and it will execute the program.
## Usage
### Commands
The script uses the following commands:

`usage: planner [-h] {add,done,view,edit,delete,clear} ...` 

Where  `{add, done, view, edit, delete, clear}`  are the available subcommands.

### Subcommands

#### `add`

Add a new task to the task list.
`planner add "Task description"` 

Example:
`planner add "Complete the project"` 

#### `done`

Mark a task as done (or mark it as incomplete).
`planner done TASK_ID` 

Where  `TASK_ID`  is the ID of the task to mark as done.

Example:
`planner done 1` 

#### `view`

View tasks. If no task ID is specified, all tasks will be displayed.
`planner view [TASK_ID]` 

Where  `TASK_ID`  is the ID of the task to view. If omitted, all tasks will be displayed.

Example:
`planner view
planner view 2` 

#### `edit`

Edit a task's description.
`planner edit TASK_ID "New task description"` 

Where  `TASK_ID`  is the ID of the task to edit.

Example:
`planner edit 1 "Updated task description"` 

#### `delete`

Delete a task by its ID.
`planner delete TASK_ID` 

Where  `TASK_ID`  is the ID of the task to delete.

Example:
`planner delete 2` 

#### `clear`
Clear all tasks in the planner. Requires confirmation.
`planner clear` 

This will ask for confirmation before clearing the task list. Type  `Y`  to confirm.
## File Structure

The task data is stored in a JSON file located at  `/Users/henrybarnes/Documents/GIT/TidyTask/tasks.json`. Each task is represented by a dictionary with the following keys:

-   **task**: The description of the task.
-   **done**: A boolean value indicating whether the task is completed.

Example content of  `tasks.json`:
`{
    "1": {
        "task": "Complete the project",
        "done": false
    },
    "2": {
        "task": "Buy groceries",
        "done": true
    }
} `

## Functions

-   **read_Json()**: Reads the tasks from  `tasks.json`  and returns the data as a dictionary.
-   **add_task(task)**: Adds a new task to the task list.
-   **view_tasks(taskID=None)**: Views all tasks or a specific task by  `taskID`.
-   **edit_task(taskID, task)**: Edits the description of an existing task.
-   **delete_task(taskID)**: Deletes a task by its ID and reshuffles remaining tasks' IDs.
-   **mark_task_done(taskID)**: Marks a task as done or toggles it between done and incomplete.
-   **clear()**: Clears all tasks from the planner.

## Notes

-   Task IDs are assigned incrementally, starting from 1.
-   The  `clear`  command asks for confirmation before deleting all tasks.
-   All commands that modify the tasks (`add`,  `edit`,  `delete`,  `done`) update the  `tasks.json`  file immediately.
