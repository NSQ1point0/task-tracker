<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" />
    <div v-show="showAddTask">
      <AddTask @toggle-add-task="toggleAddTask" @add-task="addTask" />
    </div>
    <Tasks 
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask" :tasks="tasks" 
    />
  </div>
</template>

<script>
import Header from "./components/Header"
import Tasks from "./components/Tasks"
import AddTask from "./components/AddTask"

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
  },
  data(){
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    addTask (task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "The Helium Insufficiency",
        day: "12/12/2019",
        reminder: true,
      },
      {
        id: 2,
        text: "The Parking Spot Escalation",
        day: "05/06/2019",
        reminder: true,
      },
      {
        id: 3,
        text: "The Closure Alternative",
        day: "17/04/2015",
        reminder: false
      }
    ]
  }
}
</script>

<style>
  @import './assets/css/main.css';
</style>
