<script lang="ts">
import ButtonComponent from './ButtonComponent.vue';

export default {
  name: 'HeaderItem',
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    ButtonComponent,
  },
}

</script>

<template>
  <header class="header-wrapper">
    <h1 class="green">{{ title }}</h1>
    <ButtonComponent @btn-click="$emit('toggle-add-task')" :color="showAddTask ? 'red' : 'green'"
      :text="showAddTask ? 'Close' : 'Add Task'" />
  </header>
</template>

<style scoped>
.header-wrapper {
  display: flex;
  justify-content: space-between;
}
</style>
