<template>
  <div :key="task.id" v-for="task in tasks">
    <TaskItem :task="task" />
  </div>
</template>

<script lang="ts">
import TaskItem from './TaskItem.vue'

interface Task {
  id: number;
  text: string;
  day: string;
  reminder: boolean;
}

export default {
  name: 'TasksList',
  props: {
    tasks: Array as () => Task[],
  },
  components: {
    TaskItem
  }
}
</script>
