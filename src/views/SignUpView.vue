<template>
  <main>
    <SignUp @add-user="addUser" :error="error" />
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
  data() {
    return {
      error: undefined as string | undefined,
    };
  },
  methods: {
    async addUser(loginUser: User) {
      try {
        const res = await fetch(`http://localhost:8000/signup`, {
          method: 'POST',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(loginUser)
        });
        if (!res.ok) {
          if (res.status === 400) {
            this.error = 'Email is already registered. Please use a different email.';
            return
          } else {
            throw new Error('Sign in failed. Please check your credentials.');
          }
        }
        // const data = await res.json()
        this.$router.push('/about');
      } catch (error) {
        this.error = 'Error signing up. Please try again';
      }
    }
  },
}
</script>
