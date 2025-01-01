<script setup lang="ts">
import { onMounted, ref } from 'vue';
  const status = ref('active');
  const name = ref('John Doe');
  const tasks = ref(['Task 1', 'Task 2', 'Task 3']);
  const newTask = ref("Dude");
  const toggleStatus = () => {
    if(status.value === 'active') {
      status.value = 'pending';
    } else if(status.value === 'pending') {
      status.value = 'inactive';
    } else {
      status.value = 'active';
    }  
  };
  const addTask = () => {
    if(newTask.value !== '') {
      tasks.value.push(newTask.value);
      newTask.value = '';
    }
  };

  const removeTask = (index: number) => {
    tasks.value = tasks.value.filter((task: string, i: number) => i !== index);
  }
  onMounted(async () => {
    try{
      const response = await fetch('https://jsonplaceholder.typicode.com/todos/');
      const data = await response.json();
      tasks.value = data.map((task: any) => task.title);
    }catch(err) {
      console.error(err);
    }
  });
</script>

<template>
 <h1>{{ name }}</h1>
 <p v-if="status === 'active'">User is Active</p>
 <p v-else-if="status === 'pending'">User is Pending</p>
 <p v-else>User is Inactive</p>
 <form @submit.prevent="addTask">
    <label for="newTask"></label>
    <input type="text" id="newTask" name = "newTask" v-model="newTask"/>
    <button type="submit">Add Task</button>
 </form>
 <h3>Tasks:</h3>
 <ul>
  <li v-for="(task, index) in tasks" :key="task">
    <span>{{ task }}</span> 
    <button @click="removeTask(index)">x</button>
  </li>
 </ul>
 <br>
 <button @click="toggleStatus">Change Status</button>
</template>

<style>
button {
  margin: 30px;
}
</style>

