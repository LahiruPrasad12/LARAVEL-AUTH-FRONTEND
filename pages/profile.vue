<template>
  <form @submit.prevent="updateProfile">
    <div class="mb-4 mt-10">
      <h1>View User profile</h1><hr><br>

      <div class="mb-4">
        <label for="name" class="block">Name</label>
        <input
          id="name"
          v-model="form.name"
          type="name"
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

    <button type="submit" class="border border-gray-400 py-1 px-2 rounded">
      Update
    </button>
  </form>
</template>

<script>
export default {
  data () {
    return {
      form: {
        email: this.$auth.user.email,
        name: this.$auth.user.name

      }
    }
  },
  methods: {
    async updateProfile () {
      try {
        await this.$axios.get('sanctum/csrf-cookie')
        await this.$axios.put('user/profile-information', this.form)

        await this.$auth.fetchUser()
      } catch (e) {

      }
    }
  }
}
</script>
