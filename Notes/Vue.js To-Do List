# Vue.js To-Do List 🔥

## Introduction

This guide will walk you through setting up and using a simple to-do list application using Vue.js.

## Getting Started!

### Step 1 - Project Setup in VSC

Create a Vue.js project with Vite, by simply running this command in your terminal on VSC.

```
npm create vite@latest vue-to-do list
Select Vue & JavaScript
```

Follow the commands given

```
cd vue-to-do list
npm install
npm run dev
```

This may take time some time depending on the time of your computer!

### Step 2 - Script Setup

You can use either App.vue for this application or create another component sucu as ToDoList.vue and import it into App.vue

1. Setting Up & Defining Reactive Variables

- ref() is a Vue.js function used to create a reactive reference to a value.

```
<script setup>
  import { ref } from 'vue'
```

- newTask is a reactive variable used to store the value of the task being inputted.
- tasks is a reactive variable used to store an array of tasks.

```
  const newTask = ref('')
  const tasks = ref([])
```

```
  const newTask = ref('')
  const tasks = ref([])
```
2. Adding & Removing Tasks 

-addTask() is a function that adds the task to the tasks array when called. It checks if the newTask is not empty before adding it to the tasks array.

```
  const addTask = () => {
    if (newTask.value.trim() != '') {
      tasks.value.push(newTask.value)
      newTask.value = ''
    }
  }
  const tasks = ref([])
```
- removeTask(index) is a function that removes the task at the specified index from the tasks array when called.

```
  const removeTask = (index) => {
    tasks.value.splice(index, 1)
  }
</script>
```

### Step 3 - HTML Template:

- The HTML template contains the structure of the to-do list application.
- It includes an input field for adding tasks, a button to add tasks, and a list to display tasks.

```
<template>
  <div class="todo-app">
    <!-- App title -->
    <div class="app-title">Vue-To-Do App</div>
    <!-- Task input field -->
    <div class="task-input">
      <input
        v-model="newTask"
        @keyup.enter="addTask"
        placeholder="Add new task"
      />
      <button @click="addTask">Add</button>
    </div>
    <!-- Task list -->
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="index" class="task-item">
        {{ task }}
        <button class="remove-button" @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>
```

### Step 4 - HTML Template:

- Add CSS styles as desired

```
<style scoped>
  /* CSS styles */
</style>
```

