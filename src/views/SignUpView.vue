<template>
  <main>
    <SignUp @add-user="addUser" />
  </main>
</template>

<script lang="ts">
import SignUp from '@/components/SignUp.vue';
import type { User } from './HomeView.vue';

export default {
  name: 'SignUpView',
  components: {
    SignUp
  },
  methods: {
    async addUser(loginUser: User) {
      const res = await fetch(`http://localhost:8000/signup`, {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(loginUser)
      });
      const data = await res.json()
      console.log(data)
    }
  },
}
</script>
