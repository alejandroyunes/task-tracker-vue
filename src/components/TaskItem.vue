
<script lang="ts">
import SupportIcon from './icons/IconSupport.vue'

interface Task {
  text: string;
  day: string;
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
  <div class="task">
    <h3>{{ task?.text }}
      <SupportIcon />
    </h3>
    <p>{{ task?.day }}</p>
  </div>
</template>

<style scope>
.fas {
  color: red;
}

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