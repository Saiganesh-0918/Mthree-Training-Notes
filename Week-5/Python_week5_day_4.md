# PYTHON (WEEK-5, DAY-4)

## We have brushed up all the topics and revised the execution of Angular files, how it works and how the flow is.

---

## Difference between Angular and React

### ANGULAR
- Angular is a TypeScript framework developed and maintained by Google.
- It follows the Model-View-Controller and Component-based architecture.

### **Architecture of Angular**
1. **Modules** – Organizes code into logical units.
2. **Components** – UI elements that manage the view.
3. **Services** – Handles business logic and data fetching.
4. **Templates** – HTML files that define the structure of the view.
5. **Directives** – Add dynamic behavior to templates.
6. **Dependency Injection** – Injects services and objects into components.
7. **Router** – Handles navigation between components.

---

### REACT
- React is a JavaScript library developed and maintained by Facebook.
- React mainly focuses on building UI components.
- It uses Component-based architecture and Virtual DOM to improve performance.

### **Architecture of React**
1. **Components** – UI elements that define the view.
2. **Props** – Used to pass data from parent to child components.
3. **State** – Holds data specific to a component.
4. **Virtual DOM** – React creates a virtual copy of the DOM and updates only the differences.
5. **Hooks** – Handle state, lifecycle, and context.
6. **Router** – Handles navigation between components (via React Router).

---

### **Comparison**
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20114211.png)
- Angular is structured and a solution for building complex apps.
- React is flexible and fast and is mainly used for dynamic user interfaces.

---

## Real DOM
The Real DOM is the actual structure that the browser creates based on the HTML document.

- If any update happens, then it rebuilds the whole tree, which leads to a slow and laggy process.

---

## Virtual DOM
The Virtual DOM is the lightweight copy of the Real DOM that React creates and manages in memory. It acts as the middleman between Real DOM and UI.

1. When state changes → React creates a new Virtual DOM.
2. React compares the old Virtual DOM with the new one.
3. React figures out the difference (called a "diff").
4. React updates only the changed part of the Real DOM.
5. The browser repaints the updated part.

---

### **Difference between Real and Virtual DOM**
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20123900.png)
- The performance of Real DOM is slow compared to Virtual DOM.
- React uses Virtual DOM to boost performance and update only the necessary parts.
- Angular directly modifies the Real DOM, which can lead to slower performance for frequent updates.

---

## RECONCILIATION
Reconciliation is the process of updating the user interface (UI) when the state of a web application changes.

### **Reconciliation in React**
- React uses the Virtual DOM to perform reconciliation.

**Steps:**
1. When the state changes → React creates a new Virtual DOM.
2. React compares the new Virtual DOM with the previous one (this is called diffing).
3. React finds out what’s different between the two versions.
4. It updates only the changed parts of the Real DOM (instead of rebuilding the whole tree).

---

### **Reconciliation in Angular**
- Angular does not use a Virtual DOM – it works directly with the Real DOM.
- Angular uses a technique called **Change Detection** to perform reconciliation.

**When state changes:**
1. Angular checks each component to see if the data has changed.
2. If data has changed → Angular updates the component.
3. Angular uses a process called **Zone.js** to track changes and trigger updates.
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20170532.png)

---

## Next, we moved to DSA in Python

### **STACK**
A stack is a data structure that stores and organizes data in a particular order.  
It works on the **LIFO** (Last-In-First-Out) principle. The last item added into the stack will be removed first.

**Example:**  
- In our cupboard, we organize the shirts, and the last shirt will display first and will be removed first. If we want to get another shirt, not the first one, we need to remove the last shirt and then access the required shirt.

---

### **Operations performed on Stack**
1. **Push** → Adding an element to the top of the stack.
2. **Pop** → Removing the element from the top of the stack.
3. **Peek/Top** → Viewing the element at the top of the stack without removing it.
4. **Underflow** → Trying to remove an element from an empty stack.
5. **Overflow** → Trying to add an element to a stack that’s already full (in fixed-size stacks).
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20185927.png)

---
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20190022.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20190052.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20190305.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20190343.png)
### **Flow of Execution**
1. The code creates a class named `Stack`, which performs all stack operations.
2. `__init__` → Creates an empty list to store items.
3. `is_empty` → Checks if the stack is empty.
4. `push` → Adds an element into the stack.
5. `pop` → Removes the top element from the stack.
6. `peek` → Returns the top element without removing it.
7. `size` → Returns the number of elements in the stack.
8. `__str__` → Converts the stack into a string for printing.
9. `__repr__` → Converts the stack into a string for debugging.
10. `__len__` → Returns the size of the stack.
11. `__contains__` → Checks if an element is in the stack using the `in` operator.
12. `__getitem__` → Returns the element at the specified index.
13. `__setitem__` → Modifies an element at a specific index.
14. `__delitem__` → Removes an element at a specific index.
15. `__iter__` → Allows iteration over the stack.
16. `__reversed__` → Reverses the order of elements.
17. `__eq__` and `__ne__` → Compares two stacks.
18. Comparison methods → Compare two stacks based on list order.
19. `__hash__` → Converts the list to a tuple and returns the hash value.
20. Methods not possible for a stack → Were not implemented.
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20203203.png)
---

## Next, we moved to Trees concept in DSA in Python

### **Trees**
A tree is a way to organize data in a hierarchical structure.  
It looks like an upside-down tree:

- **Root** → The top element.
- **Children** → Elements below the root.
- **Parent** → A node that has children.
- **Leaf** → A node with no children.
- **Edge** → The connection between two nodes.

---

### **Basic Structure of a Tree**
1. **Root** → Starting point (like the CEO).
2. **Node** → Each element in the tree.
3. **Child** → A node coming from another node.
4. **Parent** → A node that has children.
5. **Leaf** → A node that has no children.
6. **Edge** → The connection between two nodes.

---
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20210343.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20210444.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20210525.png)
![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20210551.png)
### **Flow of Execution**
1. `TreeNode` class performs all tree operations.
2. `__init__` → Initializes a node with a value and child nodes.
3. `add_child` → Adds a child node.
4. `remove_child` → Removes a child node.
5. `__str__` → Returns the value of the node.
6. `__repr__` → Returns a string representation.
7. `__len__` → Returns the number of children.
8. `__contains__` → Checks if a node contains a particular value.
9. `__getitem__` → Allows access to child nodes using indexing.
10. `__setitem__` → Sets child node values.
11. `__delitem__` → Deletes a child node at a particular index.
12. `__iter__` → Iterates over children.
13. `__reversed__` → Reverses iteration over children.
14. Comparison methods → Compare nodes.

![Linux Commands](../Images/Screenshots/Screenshot%202025-03-13%20212212.png)
---

## In the afternoon session, we revised all the topics and solved a few HackerRank problems on Python.
![Linux Commands](../Images/Screenshots/Screenshot%20(99).png)
![Linux Commands](../Images/Screenshots/Screenshot%20(100).png)
---

