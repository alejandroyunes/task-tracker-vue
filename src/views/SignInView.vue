<template>
  <main>
    <SignIn @add-user="addUser" />
  </main>
</template>

<script lang="ts">
import SignIn from '@/components/SignIn.vue';
import type { User } from './HomeView.vue';

export default {
  name: 'HomeVue',
  components: {
    SignIn
  },
  methods: {
    addUser(loginUser: User) {
      console.log(loginUser)
    }
  },
}
</script>

