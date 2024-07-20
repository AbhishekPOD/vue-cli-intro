<template>
  <div class="container">
    <Header @add-task="addTask" title="My Todo List" />
    <Tasks
      @delete-task="deleteTask" 
      :tasks="tasks"
    />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  data () {
    return {
      tasks: [
        {
          id: 1,
          text: 'Do something 1'
        },
        {
          id: 2,
          text: 'Do something 2'
        },
        {
          id: 3,
          text: 'Do something 3'
        },
        {
          id: 4,
          text: 'Do something 4'
        },
      ]
    }
  },
  components: {
    Header,
    Tasks,
    Footer
  },
  methods: {
    deleteTask (id) {
      // this.tasks = this.tasks.filter(task => task.id != id);

      const index = this.tasks.findIndex(task => task.id == id);

      this.tasks.splice(index, 1);
    },

    addTask (task) {
      const id = Math.floor(Math.random() * 10000) + 1;
      const newTask = { id, text: task };

      this.tasks = [...this.tasks, newTask];
      // this.tasks.push(newTask);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>

<!-- -- App.vue
  -- Header
   -- Button
  -- Tasks
    -- Task
  -- Footer -->