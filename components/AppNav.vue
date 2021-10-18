<template>
  <ul>
    <li>
      <nuxt-link :to="{ name: 'index' }" class="px-2">
        Home
      </nuxt-link>
      <template v-if="$auth.loggedIn">
        <l1>
          <a href="">{{ $auth.user.name }}</a>
        </l1>
        <l1>
          <a href="">Dash board</a>
        </l1>
        <l1>
          <a href="">Logout</a>
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
