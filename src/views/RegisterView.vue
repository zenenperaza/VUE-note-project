<template>
    <div class="content mx-auto" style="max-width: 500px;"> 
        <h1>Register</h1>
        <form>
            
  <div class="mb-3">
    <label for="name" class="form-label">Name</label>
    <input type="text" class="form-control" id="name" aria-describedby="emailHelp" v-model="name">
  </div>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" v-model="email">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" class="form-control" id="exampleInputPassword1" v-model="password">
  </div>

  <button type="submit" class="btn btn-primary" v-on:click.prevent="creaUser">Submit</button>
</form>
<div class="alert alert-primary" role="alert">
  {{ feedback }}
</div>
    </div>
    </template>
    
    <script lang="ts" setup>
    import { ref } from 'vue';
    import useAuth from '@/store/auth'
    import router from '@/router';

    const store = useAuth()
    const name = ref('')
    const email = ref('')
    const password = ref('')
    const feedback = ref('')

    const creaUser = async () => {
        feedback.value = "Procesando... Espere, por favor"
        const response = await store.register(name.value, email.value, password.value)
        if (response == false) {
            feedback.value = "Error al regsitrarse."
        } else {
            router.push({name: 'list'})
        }
    }
       
    </script>
    
    <style scoped>
    
    </style>