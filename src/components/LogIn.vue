<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Email</label>
      <input type="text" v-model="email" name="email" placeholder="Email" />
    </div>
    <div class="form-control">
      <label>Password</label>
      <input type="password" v-model="password" name="password" placeholder="Password" />
    </div>
    <p v-if="error !== null" class="error-message">{{ error }}</p>

    <input type="submit" value="Login" class="btn btn-block" />
    
    <RouterLink :to="{ path: '/signup' }" class="signIn">
      <input value="Sign up" class="btn btn-block btn-sign" />
    </RouterLink>
  </form>
</template>

<script lang="ts">

export default {
  name: 'LogIn',
  props: {
    error: String, 
  },
  data() {
    return {
      email: '',
      password: '',
    }
  },
  methods: {
    onSubmit(e: Event) {
      e.preventDefault()
      if (!this.email || !this.password) {
        alert('Please add email or password')
        return
      }

      const loginUser = {
        email: this.email,
        password: this.password,
      }
      this.$emit('login-user', loginUser)

      this.email = ''
      this.password = ''
    }
  },
  emits: ['login-user']
}
</script>

<style scoped>

.error-message {
  color: red;
  padding-left: 8px;
}

.btn {
  display: inline-block;
  color: #fff;
  background: black;
  border: none;
  padding: 10px 20px;
  margin: 5px 5px 15px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
  text-align: center;
}

.btn-sign {
  background: green;
}

.signIn {
  text-decoration: none;
}

.btn-block {
  display: block;
  width: 100%;
}

.add-form {
  margin-bottom: 40px;
}

.form-control {
  margin: 20px 0;
}

.form-control label {
  display: block;
}

.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}

.form-control-check label {
  flex: 1;
}

.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>