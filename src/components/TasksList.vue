<template>
  <div :key="task.id" v-for="task in tasks">
    <TaskItem @toggle-reminder="$emit('toggle-reminder', task.id)" @delete-task="$emit('delete-task', task.id)"
      :task="task" />
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
  },
  emits: ['delete-task', 'toggle-reminder']
}
</script>
