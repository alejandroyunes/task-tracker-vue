<template>
  <div class="container">
    <HeaderItem title="task tracker" />
    <TasksList @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
    <RouterView />
  </div>
</template>

<script  lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HeaderItem from './components/HeaderItem.vue'
import TasksList from './components/TasksList.vue'

export default {
  name: 'App',
  components: {
    HeaderItem,
    TasksList
  },

  data() {
    return {
      tasks: [] as { id: number; text: string; day: string; reminder: boolean }[],
    }
  },
  methods: {
    deleteTask(id: number) {
      if (confirm('Are you sure')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id: number) {
      console.log('toggle:', id)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'dr appointment',
        day: 'March 1st at 2:30p',
        reminder: true
      },
      {
        id: 2,
        text: 'gym',
        day: 'March 1st at 2:30p',
        reminder: true
      },
      {
        id: 3,
        text: 'walk dog',
        day: 'March 1st at 2:30p',
        reminder: false
      }
    ]
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
