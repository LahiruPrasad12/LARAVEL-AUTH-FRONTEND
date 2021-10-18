<template>
  <form @submit.prevent="login">
    <div class="mb-4 mt-10">
      <h1>Login Page</h1><hr><br>

      <label for="email" class="block">Email</label>
      <input
        id="email"
        v-model="form.email"
        type="text"
        name="email"
        placeholder="Enter Email"
        class="border border-gray-400 py-1 px-2 rounded"
      >
    </div>
    <div class="mb-4">
      <label for="password" class="block">Password</label>
      <input
        id="password"
        v-model="form.password"
        type="password"
        name="password"
        placeholder="Enter Password"
        class="border border-gray-400 py-1 px-2 rounded"
      >
    </div>

    <button type="submit" class="border border-gray-400 py-1 px-2 rounded">
      Login
    </button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      form: {
        email: '',
        password: ''

      }
    }
  },
  methods: {
    async login () {
      try {
        await this.$auth.loginWith('laravelSanctum', {
          data: this.form
        })
      } catch (e) {

      }
    }
  }
}
</script>
