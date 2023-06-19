<template>
  <nav>
  <router-link :to="{name: 'login'}">Login</router-link> |
  <router-link :to="{name: 'register'}">Register</router-link> |
  <router-link :to="{name: 'list'}">Notes List</router-link>  |
  <router-link :to="{name: 'create'}">Notes Create</router-link>   |
  <button v-on:click.prevent="logout">Logout</button> 
</nav>
<router-view></router-view>
</template>

<script lang="ts" setup>
import router from './router'
import useAuth from './store/auth'

const store = useAuth()

 const logout = () => {
  store.logout() 
  router.push({name: 'login'})
 }
</script>

<style scoped>

</style>
