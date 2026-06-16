# 📌 TaskFlow Kanban Board

A fully interactive **Kanban Task Management Dashboard** built with **HTML, CSS, and Vanilla JavaScript**. The application allows users to create, edit, delete, organize, and drag-and-drop tasks across multiple swimlanes and workflow stages while persisting data using **Local Storage**.

---

# 🚀 Features

### ✅ Task Management

* Create new tasks
* Edit existing tasks
* Delete tasks
* Assign task titles and descriptions
* Select task colors for visual categorization

### ✅ Kanban Workflow

Tasks move through three workflow stages:

```text
To Do → In Progress → Done
```

### ✅ Swimlane Organization

Tasks are grouped into separate swimlanes:

```text
Critical
Issues
Maintenance
```

This helps categorize work based on priority or type.

### ✅ Drag & Drop

Supports native HTML5 drag-and-drop functionality.

Users can:

* Drag tasks between columns
* Move tasks across swimlanes
* Instantly update task status

### ✅ Persistent Storage

Uses browser Local Storage.

Tasks remain available even after:

* Browser refresh
* Closing and reopening the tab
* Restarting the browser

### ✅ Responsive Design

Works on:

* Desktop
* Laptop
* Tablet
* Mobile devices

---

# 📸 Application Workflow

```text
+-------------------------------+
|        Task Dashboard         |
+-------------------------------+

Critical
 ├── To Do
 ├── In Progress
 └── Done

Issues
 ├── To Do
 ├── In Progress
 └── Done

Maintenance
 ├── To Do
 ├── In Progress
 └── Done
```

---

# 🏗 Project Architecture

```text
TaskFlow
│
├── HTML
│   ├── Dashboard Layout
│   ├── Task Modal
│   └── Form Elements
│
├── CSS
│   ├── Board Styling
│   ├── Swimlanes
│   ├── Task Cards
│   ├── Responsive Layout
│   └── Animations
│
└── JavaScript
    ├── State Management
    ├── Rendering Engine
    ├── Drag & Drop
    ├── Local Storage
    ├── Task CRUD Operations
    └── Event Handling
```

---

# 🛠 Technologies Used

| Technology            | Purpose          |
| --------------------- | ---------------- |
| HTML5                 | Structure        |
| CSS3                  | Styling          |
| JavaScript ES6        | Functionality    |
| Local Storage API     | Data Persistence |
| HTML5 Drag & Drop API | Task Movement    |

---

# 📂 Project Structure

```text
project/
│
├── index.html
├── style.css
├── script.js
└── README.md
```

---

# 📊 Data Model

Each task is stored as an object.

```javascript
{
    id: 1718553642731,
    title: "Fix Login Bug",
    description: "Authentication issue",
    swimlane: "critical",
    status: "todo",
    color: "#ffb3b3"
}
```

---

# 🧠 State Management

The application maintains all task data inside a central state object.

```javascript
const state = {
    tasks: []
};
```

### Responsibilities

* Stores all tasks
* Updates task information
* Handles drag-and-drop changes
* Syncs data with Local Storage

---

# 💾 Local Storage Implementation

### Save State

```javascript
localStorage.setItem(
    STORAGE_KEY,
    JSON.stringify(state)
);
```

### Load State

```javascript
const saved =
    localStorage.getItem(STORAGE_KEY);
```

Benefits:

* No database required
* Instant persistence
* Works offline

---

# 🎯 Core Functionalities

---

## 1. Create Task

Users can add tasks through a modal form.

### Stored Fields

* Title
* Description
* Swimlane
* Color

Example:

```javascript
const newTask = {
    id: Date.now(),
    title: titleInput.value,
    description: descInput.value,
    swimlane: swimlaneSelect.value,
    status: 'todo',
    color: colorInput.value
};
```

---

## 2. Edit Task

Existing tasks can be modified.

Workflow:

```text
Click Edit
      ↓
Open Modal
      ↓
Load Task Data
      ↓
Modify Fields
      ↓
Save Changes
```

The application uses:

```javascript
let editingTaskId = null;
```

to determine whether the form is in:

```text
Create Mode
```

or

```text
Edit Mode
```

---

## 3. Delete Task

Tasks can be permanently removed.

Implementation:

```javascript
state.tasks =
state.tasks.filter(
    t => t.id != taskId
);
```

Process:

```text
Find Task
    ↓
Exclude From Array
    ↓
Save State
    ↓
Re-render Board
```

---

## 4. Drag & Drop

### Drag Start

Stores the task ID.

```javascript
e.dataTransfer.setData(
    'text/plain',
    task.id
);
```

---

### Drop

Retrieves:

```javascript
const taskId =
e.dataTransfer.getData('text/plain');
```

and updates:

```javascript
updateTaskLocation(
    taskId,
    newSwimlane,
    newStatus
);
```

---

## 5. Rendering Engine

The board is generated dynamically.

Workflow:

```text
Load Tasks
      ↓
Filter Tasks
      ↓
Create Task Elements
      ↓
Append To Cells
      ↓
Display Board
```

---

# 🔄 Task Lifecycle

```text
Create Task
      ↓
To Do
      ↓
In Progress
      ↓
Done
      ↓
Delete (Optional)
```

---

# 🎨 User Interface Components

## Header

Contains:

* Application title
* Dashboard controls

---

## Swimlane Header

Displays:

```text
Critical
Issues
Maintenance
```

and

```text
+ Add Task
```

button.

---

## Task Card

Displays:

* Task title
* Description
* Edit button
* Delete button

---

## Modal Form

Used for:

* Creating tasks
* Editing tasks

Fields:

```text
Title
Description
Swimlane
Color
```

---

# 🔧 Important JavaScript Concepts Used

### Arrays

```javascript
filter()
find()
forEach()
push()
```

---

### DOM Manipulation

```javascript
createElement()
appendChild()
querySelector()
classList.add()
classList.remove()
```

---

### Event Handling

```javascript
click
dragstart
dragover
dragleave
drop
```

---

### Dataset API

```javascript
cell.dataset.swimlane
cell.dataset.column
```

Used to identify target cells during drag-and-drop.

---

# 📈 Performance Considerations

* Lightweight architecture
* No external libraries
* Minimal memory usage
* Fast rendering
* Suitable for small and medium-sized projects

---

# 🔐 Future Enhancements

### Authentication

* User accounts
* Login system

### Backend Integration

* Node.js
* Express.js
* MongoDB

### Team Collaboration

* Multiple users
* Shared boards

### Notifications

* Due date reminders
* Task alerts

### Analytics Dashboard

* Productivity metrics
* Completion reports

### Search & Filter

* Search tasks
* Filter by swimlane
* Filter by status

---

# 🧪 Testing Checklist

### Task Creation

* [ ] Add new task
* [ ] Validate empty fields

### Task Editing

* [ ] Edit title
* [ ] Edit description
* [ ] Edit color

### Task Deletion

* [ ] Delete task
* [ ] Verify Local Storage update

### Drag & Drop

* [ ] Move within swimlane
* [ ] Move across swimlanes
* [ ] Move across statuses

### Persistence

* [ ] Refresh page
* [ ] Verify tasks remain

---

# 🤝 Contributing

Contributions are welcome.

Steps:

```bash
# Fork repository

# Clone repository
git clone https://github.com/your-username/taskflow-kanban-board.git

# Create branch
git checkout -b feature-name

# Commit changes
git commit -m "Added feature"

# Push changes
git push origin feature-name
```

Create a Pull Request for review.

---

# 📜 License

This project is licensed under the MIT License.

---

# 👨‍💻 Author

**TaskFlow Kanban Board**

Built using **HTML, CSS, JavaScript, Local Storage, and HTML5 Drag & Drop API** to demonstrate frontend development, state management, DOM manipulation, and browser-based persistence. ⭐

If you found this project useful, consider giving it a star on GitHub.
