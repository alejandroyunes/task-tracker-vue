<script lang="ts">
import ButtonComponent from './ButtonComponent.vue';

export default {
  name: 'HeaderItem',
  props: {
    title: String
  },
  components: {
    ButtonComponent,
  },
}

</script>

<template>
  <header class="header-wrapper">
    <h1 class="green">{{ title }}</h1>
    <ButtonComponent text="Add task" color="green" />
  </header>
</template>

<style scoped>
.header-wrapper {
  display: flex;
  justify-content: space-between;
}
</style>
