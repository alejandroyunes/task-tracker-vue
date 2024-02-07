<template>
  <div class="container">
    <HeaderItem @toggle-add-task="toggleAddTask" title="task tracker" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TasksList @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
    <RouterView />
  </div>
</template>

<script  lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HeaderItem from './components/HeaderItem.vue'
import TasksList from './components/TasksList.vue'
import AddTask from './components/AddTask.vue'
import type { Task } from './components/TaskItem.vue'

export default {
  name: 'App',
  components: {
    HeaderItem,
    TasksList,
    AddTask
  },

  data() {
    return {
      tasks: [] as Task[],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask
    },
    async addTask(task: Task) {
      const res = await fetch(`http://localhost:8000/tasks/`, {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task)
      });
      const data = await res.json()

      this.tasks = [...this.tasks, data]
    },
    async deleteTask(id: number) {
      if (confirm('Are you sure')) {
        const res = await fetch(`http://localhost:8000/tasks/${id}`, {
          method: 'DELETE'
        })
        res.status === 200 ? (this.tasks = this.tasks.filter((task) => task.id !== id)) : alert('Error deleting task')
      }
    },
    async toggleReminder(id: number) {
      const taskToToggle = await this.fetchTask(id)
      const updTask = { ...taskToToggle, reminder: !taskToToggle.reminder }

      const res = await fetch(`http://localhost:8000/tasks/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updTask),
      })

      const data = await res.json()

      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: data.reminder } : task
      )
    },
    async fetchTasks() {
      const res = await fetch("http://localhost:8000/tasks");
      const data = await res.json()
      return data
    },
    async fetchTask(id: number) {
      const res = await fetch(`http://localhost:8000/tasks/${id}`);
      const data = await res.json()
      return data
    }
  },
  async created() {
    this.tasks = await this.fetchTasks()
  },
}

</script>

<style scoped>
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
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
</style>
