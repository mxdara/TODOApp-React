# Todo List Application

This repository contains a simple todo list application built with React. The application allows users to add, toggle, and delete todo items. The state of the todos is synchronized with the local storage, ensuring data persistence across page reloads.

## Function Logic

1. `useState` Hook and Local Storage:
   - The code starts by importing the `useEffect` and `useState` hooks from React.
   - It declares a state variable called `todos` using the `useState` hook. The initial state is set by using a function that retrieves data from the local storage. If there are no items in the local storage, an empty array is used as the initial state.

2. `useEffect` Hook for Local Storage Synchronization:
   - The `useEffect` hook is used to synchronize the `todos` state with the local storage.
   - It watches for changes in the `todos` state (provided as the second argument to the `useEffect` hook) and triggers the effect whenever the state changes.
   - Inside the `useEffect`, the `localStorage.setItem` method is used to store the updated `todos` state in the local storage. The `JSON.stringify` function is used to convert the state data to a JSON string before storing it.

3. `addTodo` Function:
   - The `addTodo` function is used to add a new todo item to the `todos` state.
   - When called, it takes a `title` as an argument, which represents the title of the new todo item.
   - It uses the `setTodos` function to update the state. It takes a callback function that receives the current state (`currentTodos`) and returns the updated state.
   - In this case, the function creates a new todo object with a unique `id`, the provided `title`, and a default `completed` value of `false`.
   - The new todo object is then appended to the current todos using the spread operator (`...currentTodos`), and the updated state is set with `setTodos`.

4. `toggleTodo` Function:
   - The `toggleTodo` function is used to toggle the `completed` status of a todo item with a given `id`.
   - When called, it takes `id` and `completed` as arguments. `id` represents the unique identifier of the todo item, and `completed` represents the new `completed` status for the todo item.
   - It also uses the `setTodos` function with a callback to update the state.
   - The function maps through the current todos (`currentTodos`) using `currentTodos.map(todo => { ... })`.
   - If the `id` of the current todo matches the provided `id`, it returns a new todo object with the updated `completed` status. Otherwise, it returns the original todo object unchanged.

5. `deleteTodo` Function:
   - The `deleteTodo` function is used to remove a todo item with a specific `id` from the `todos` state.
   - When called, it takes the `id` of the todo item to be deleted as an argument.
   - Similar to the previous functions, it uses the `setTodos` function with a callback to update the state.
   - The function uses `currentTodos.filter(todo => todo.id !== id)` to filter out the todo item with the provided `id` from the `currentTodos`, effectively deleting it from the state.

## Components

The main `App` component renders the following components:
- `NewTodoForm`: Allows users to input a new todo item and submit it. It calls the `addTodo` function when a new todo is submitted.
- `TodoList`: Displays the list of todos. It takes the `todos` state as a prop and renders each todo item accordingly. It also provides the `toggleTodo` and `deleteTodo` functions as props to handle toggling and deleting todos.

By using these functions and components together, the app can manage a list of todos, add new todos, mark them as completed, and delete them from the list. The state of the todos is synchronized with the local storage, ensuring that the data persists across page refreshes or visits.