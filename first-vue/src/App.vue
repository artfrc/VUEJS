<script setup>

import { ref } from 'vue';

  const name = ref('John Doe');
  const status = ref('active');
  const tasks = ref(['Task One', 'Task Two', 'Task Three']);
  const newTask = ref('');

  const toogleStatus = () => {
      if(status.value === 'active') status.value = 'pending'
      else if(status.value === 'pending') status.value = 'inactive'
      else status.value = 'active';
  };

  const addTask = () => {
    if(newTask.value.trim() !== '') {
      tasks.value.push(newTask.value);
      newTask.value = '';
    };

  }

  const deleteTask = () => {
    
  }
</script>

<template>
  <h1>{{  name }}</h1>,
  <p v-if=" status === 'active' ">User is active!</p>
  <p v-else-if=" status === 'pending'">User is pending</p>
  <p v-else>User is inactive</p> <br>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task: </label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>
  <br>

  <h2>Tasks:</h2> <br>

  <ul>
    <li v-for="(index, task) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul> <br>

  <button @click="toogleStatus">Change Status</button>

</template>
