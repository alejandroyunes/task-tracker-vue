<template>
  <div class="container">
    <h1 class="main-title"> Task Tracker</h1>
    <RouterView />
  </div>
</template>

<script  lang="ts">

export default {
  name: 'App',
  components: {},
  data() {
    return {}
  },
  methods: {},
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
  padding: 30px;
  border-radius: 5px;
}
.main-title {
  display: flex;
  justify-content: center;
  margin-bottom: 24px;
}
</style>
