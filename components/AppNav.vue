<template>
  <ul>
    <li>
      <nuxt-link :to="{ name: 'index' }" class="px-2">
        Home
      </nuxt-link>
      <template v-if="$auth.loggedIn">
        <l1>
          <nuxt-link :to="{name:'profile'}">
            {{ $auth.user.name }}
          </nuxt-link>
        </l1>
        <l1>
          <nuxt-link :to="{name:'dashboard'}">
            Dash board
          </nuxt-link>
        </l1>
        <l1>
          <a href="#" @click="logout">Logout</a>
        </l1>
      </template>
      <template v-if="!$auth.loggedIn">
        <l1>
          <nuxt-link :to="{name:'login'}" class="px-2">
            Login
          </nuxt-link>
        </l1>
        <l1>
          <nuxt-link :to="{name:'register'}" class="px-2">
            Register
          </nuxt-link>
        </l1>
      </template>
    </li>
  </ul>
</template>

<script>
export default {
  methods: {
    async logout () {
      await this.$auth.logout()
      this.$router.replace({ name: 'login' })
    }
  }
}
</script>
