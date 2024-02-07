<template>
  <main>
    <LogIn @login-user="loginUser" :error="error"/>
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
  data() {
    return {
      error: undefined as string | undefined,
    };
  },
  methods: {
    async loginUser(loginUser: User) {
      try {
        const res = await fetch(`http://localhost:8000/signin/`, {
          method: 'POST',
          headers: {
            'Content-type': 'application/json',
          },
          body: JSON.stringify(loginUser)
        });

        if (!res.ok) {
          throw new Error('Sign in failed. Please check your credentials.');
        }

        const data = await res.json();
        console.log(data);

        this.$router.push('/about');
        this.error = undefined;
      } catch (error) {
        console.error(error);
        this.error = 'Error signing in. Please try again.';
      }
    },
  }
}
</script>

