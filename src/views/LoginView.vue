<template>
    <div class="content m-3 mx-auto" style="max-width: 500px;"> 
        <h1>Login</h1>
        <form>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="email">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" class="form-control" id="exampleInputPassword1" v-model="password">
  </div>

  <button type="submit" class="btn btn-primary" v-on:click.prevent="loginUser">Submit</button>
</form>
<div class="alert alert-primary" role="alert">{{feedback}}</div>
    </div>
    <router-link :to="{name: 'register'}">Register</router-link>
    </template>

    <script lang="ts" setup>
       import { ref } from 'vue'
       import useAuth from '@/store/auth'
       import router from '@/router';

       const store = useAuth()
       const email = ref('')
       const password = ref('')
       const feedback = ref('')

       const loginUser = async () => {
        feedback.value = "Validando la informacion... Espere, por favor."
        const response = await store.login(email.value, password.value)
           if (response == false) {
            feedback.value = "Error al ingresar."
           } else {
            router.push({name: 'list'})
           } 
       }


    </script>
    
    <style scoped>
    
    </style>