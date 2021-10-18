<template>
  <form @submit.prevent="register">
    <div class="mb-4 mt-10">
      <h1>Register Page</h1><hr><br>
      <div class="mb-4">
        <label for="name" class="block">name</label>
        <input
          id="name"
          v-model="form.name"
          type="text"
          name="name"
          placeholder="Enter name"
          class="border border-gray-400 py-1 px-2 rounded"
        >
      </div>
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
    <div class="mb-4">
      <label for="password_confirmation" class="block">Password Confirmation</label>
      <input
        id="password"
        v-model="form.password_confirmation"
        type="password"
        name="password_confirmation"
        placeholder="Confirm Password"
        class="border border-gray-400 py-1 px-2 rounded"
      >
    </div>
    <button type="submit" class="border border-gray-400 py-1 px-2 rounded">
      Register
    </button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      form: {
        email: '',
        password: '',
        name: '',
        password_confirmation: ''
      }
    }
  },
  methods: {
    async register () {
      try {
        await this.$axios.get('sanctum/csrf-cookie')
        await this.$axios.post('register', this.form)
        await this.$auth.loginWith('laravelSanctum', {
          data: this.form
        })
      } catch (e) {
        alert(e.message)
      }
    }
  }
}
</script>
