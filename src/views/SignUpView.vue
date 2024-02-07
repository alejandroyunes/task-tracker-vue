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
    addUser(loginUser: User) {
      console.log(loginUser)
    }
  },
}
</script>

