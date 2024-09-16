<script setup>
import {onMounted, ref} from 'vue';

const name = ref('Will Zapata');
const status = ref('active');
const tasks = ref([
  'Task 1', 'Task 2', 'Task 3'
]);
const newTask = ref('');

const toggleStatus = () => {
  status.value = status.value === 'active' ? 'pending' : 'active'
};
const addTask = () => {
  if (newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
}
const deleteTask = (index) => {
  tasks.value.splice(index, 1);
}

onMounted(async () => {
  try {
    const response  =await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await response.json();
    tasks.value = data.map(((task) => task.title));
  } catch (e) {
    console.error('Error fetching tasks ' + e);
  }
});
</script>


<template>
  <h1>{{ name }}</h1>
  <br/>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <br/>

  <div>
    <form @submit.prevent="addTask" id="form-task">
      <label for="newTask">Add Task</label><br/>
      <input type="text" id="newTask" name="newTask" v-model="newTask">
    </form>

    <button type="submit" form="form-task">Submit</button>
  </div>

  <br/>
  <br/>

  <div>
    <h3>Tasks:</h3>

    <br/>

    <ol>
      <li v-for="(task, index) in tasks" :key="index">
        <span>{{ task }}</span>
        <button @click="deleteTask(index)">X</button>
      </li>
    </ol>


    <br/>
    <!-- <button v-on:click="toggleStatus">Change Status</button> -->
    <button @click="toggleStatus">Change Status</button>
  </div>

  <br/>
</template>
