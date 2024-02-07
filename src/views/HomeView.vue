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
    async loginUser(loginUser: User) {
      const res = await fetch(`http://localhost:8000/signin/`, {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(loginUser)
      });
      const data = await res.json()
      console.log(data)
    },
  }
}
</script>


