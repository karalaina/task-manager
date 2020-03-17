<template>
  <main>
    <h1>Task Manager</h1>
    <h2>To Do</h2>
    <div v-for="task in msg.tasks" :key="task">
      {{ task }}
      <button>Edit</button>
      <button>Delete</button>
    </div>
  </main>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Home',
  data() {
    return {
      msg: [],
    };
  },
  methods: {
    getMessage() {
      const path = 'http://localhost:5000/';
      axios.get(path)
        .then((res) => {
          this.msg = res.data;
        })
        .catch((error) => {
          // eslint-disable-next-line
          console.error(error);
        });
    },
  },
  created() {
    this.getMessage();
  },
};
</script>
