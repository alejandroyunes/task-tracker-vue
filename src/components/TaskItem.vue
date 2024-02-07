
<script lang="ts">
import SupportIcon from './icons/IconDelete.vue'

export interface Task {
  id: number
  text: string
  day: string
  reminder: boolean
}

export default {
  name: 'TaskItem',
  props: {
    task: Object as () => Task,
  },
  components: {
    SupportIcon
  }
}
</script>

<template>
  <div @dblclick="$emit('toggle-reminder', task?.id)" :class="[task?.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task?.text }}
      <SupportIcon @click="$emit('delete-task', task?.id)" />
    </h3>
    <p>{{ task?.day }}</p>
  </div>
</template>

<style scope>

.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}

.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
  color: black;
}

.task p {
  color: black
}
</style>