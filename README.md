# Ex03 To-Do List using JavaScript
## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do App</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      min-height: 100vh;
      background-color: #f4f4f4;
      margin: 0;
    }

    .todo-app {
      background: white;
      padding: 20px;
      border-radius: 10px;
      width: 380px;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
    }

    h1 {
      text-align: center;
      margin-bottom: 20px;
    }

    .input-container {
      display: flex;
      gap: 10px;
      margin-bottom: 15px;
    }

    #todo-input {
      flex: 1;
      padding: 8px;
      border-radius: 5px;
      border: 1px solid #ccc;
      font-size: 16px;
    }

    #add-btn {
      padding: 8px 12px;
      border: none;
      background-color: #28a745;
      color: white;
      border-radius: 5px;
      cursor: pointer;
      font-weight: bold;
    }

    #add-btn:hover {
      background-color: #218838;
    }

    ul {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 5px;
      border-bottom: 1px solid #eee;
      font-size: 16px;
    }

    li span {
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
    }

    li.completed span {
      text-decoration: line-through;
      color: gray;
    }

    button.edit-btn {
      margin-right: 5px;
      background-color: #ffc107;
      border: none;
      padding: 5px 8px;
      border-radius: 3px;
      cursor: pointer;
    }

    button.edit-btn:hover {
      background-color: #e0a800;
    }

    button.delete-btn {
      background-color: #dc3545;
      border: none;
      padding: 5px 8px;
      border-radius: 3px;
      cursor: pointer;
    }

    button.delete-btn:hover {
      background-color: #c82333;
    }

    .filters {
      margin-top: 15px;
      display: flex;
      justify-content: flex-end;
      flex-wrap: wrap;
    }

    #clear-all {
      padding: 5px 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      background-color: #007bff;
      color: white;
      font-weight: bold;
    }

    #clear-all:hover {
      opacity: 0.8;
    }

    .checkmark {
      color: #28a745;
      font-weight: bold;
    }

    footer {
      margin-top: 15px;
      font-size: 14px;
      color: #555;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="todo-app">
    <h1>My To-Do List</h1>
    <div class="input-container">
      <input type="text" id="todo-input" placeholder="Add a new task">
      <button id="add-btn">Add</button>
    </div>
    <ul id="todo-list"></ul>
    <div class="filters">
      <button id="clear-all">Clear All</button>
    </div>
  </div>

  <footer>
    Created by Oviya N
  </footer>

  <script>
    const input = document.getElementById("todo-input");
    const addBtn = document.getElementById("add-btn");
    const todoList = document.getElementById("todo-list");
    const clearAllBtn = document.getElementById("clear-all");

    let tasks = JSON.parse(localStorage.getItem("tasks")) || [];
    renderTasks(tasks);

    addBtn.addEventListener("click", () => {
      const taskText = input.value.trim();
      if (taskText === "") return;
      const task = { text: taskText, completed: false };
      tasks.push(task);
      saveTasks();
      renderTasks(tasks);
      input.value = "";
    });

    clearAllBtn.addEventListener("click", () => {
      tasks = [];
      saveTasks();
      renderTasks(tasks);
    });

    function renderTasks(tasksArray) {
      todoList.innerHTML = "";
      tasksArray.forEach((task, index) => {
        const li = document.createElement("li");
        const span = document.createElement("span");
        span.innerHTML = task.completed 
          ? `<span class="checkmark">&#10003;</span> ${task.text}` 
          : task.text;
        if(task.completed) li.classList.add("completed");
        span.addEventListener("click", () => {
          tasks[index].completed = !tasks[index].completed;
          saveTasks();
          renderTasks(tasks);
        });
        const editBtn = document.createElement("button");
        editBtn.textContent = "Edit";
        editBtn.className = "edit-btn";
        editBtn.addEventListener("click", () => {
          const newText = prompt("Edit task:", task.text);
          if(newText !== null && newText.trim() !== "") {
            tasks[index].text = newText.trim();
            saveTasks();
            renderTasks(tasks);
          }
        });
        const deleteBtn = document.createElement("button");
        deleteBtn.textContent = "Delete";
        deleteBtn.className = "delete-btn";
        deleteBtn.addEventListener("click", () => {
          tasks.splice(index, 1);
          saveTasks();
          renderTasks(tasks);
        });
        li.appendChild(span);
        li.appendChild(editBtn);
        li.appendChild(deleteBtn);
        todoList.appendChild(li);
      });
    }

    function saveTasks() {
      localStorage.setItem("tasks", JSON.stringify(tasks));
    }
  </script>
</body>
</html>
```

## OUTPUT
<img width="1909" height="1016" alt="image" src="https://github.com/user-attachments/assets/92216fe1-960f-425e-8e39-388fc373f379" />

<img width="1915" height="947" alt="image" src="https://github.com/user-attachments/assets/aabbb7f9-16f9-43b9-a265-e46f095f6bb1" />

## RESULT
The program for creating To-do list using JavaScript is executed successfully.
