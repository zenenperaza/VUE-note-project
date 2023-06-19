<template>
  <nav>
  <router-link :to="{name: 'login'}">Login</router-link> |
  <router-link :to="{name: 'register'}">Register</router-link> |
  <router-link :to="{name: 'list'}">Notes List</router-link>  |
  <router-link :to="{name: 'create'}">Notes Create</router-link> 
</nav>
<router-view></router-view>
</template>

<script lang="ts" setup>
 
</script>

<style scoped>

</style>
