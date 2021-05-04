<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Tugas Pemula"
    :showAddTask="showAddTask" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" 
    @delete-task="deleteTask" :tasks="tasks" />
  </div>

</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },

  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },

  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      // console.log('task', id);
      if (confirm('Apakah kamu yakin menghapus?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      // console.log(id)
      this.tasks = this.tasks.map((task) => task.id === id
      ? {...task, reminder: !task.reminder} : task)
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        notes: 'Membuat rest API Laravel',
        time: '28 April 2021',
        reminder: true,
      },
      {
        id: 2,
        notes: 'Membuat komponen di Vue Js',
        time: '3 Mei 2021',
        reminder: false,
      },
      {
        id: 3,
        notes: 'Menghosting Inventaris PKL',
        time: '30 April 2021',
        reminder: true,
      },
      {
        id: 4,
        notes: 'Deploy ke server Linux Ubuntu',
        time: '5 Mei 2021',
        reminder: false,
      },
    ]
  }
}
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */

@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid #5e60ce;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000000;
  color: #ffffff;
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
