<script>
export default {
  data() {
    return {
      name: 'William Zapata',
      status: 'pending',
      tasks: [
        { name: 'Task 1', completed: true },
        { name: 'Task 2', completed: false },
        { name: 'Task 3', completed: true },
      ],
      link: 'https://www.google.com',
    }
  },
  methods: {
    toggleStatus() {
      this.status = this.status === 'active' ? 'pending' : 'active'
    }
  }
}
</script>



<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <h3>Tasks:</h3>

  <ol>
    <li v-for="task in tasks" :key="task.name">
      <span>{{ task.name }}</span>
    </li>
  </ol>

  <!-- <a v-bind:href="link">Google</a> -->
  <a :href="link">Google</a>

  <br />
  <!-- <button v-on:click="toggleStatus">Change Status</button> -->
  <button @click="toggleStatus">Change Status</button>
</template>
