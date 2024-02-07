<template>
  <main>
    <LogIn @login-user="loginUser" />
  </main>
</template>

<script lang="ts">
import LogIn from '@/components/LogIn.vue';

export interface User {
  email: string
  password: string
}

export default {
  name: 'HomeVue',
  components: {
    LogIn
  },
  methods: {
    loginUser(loginUser: User) {
      console.log(loginUser)
    },
  }
}
</script>


