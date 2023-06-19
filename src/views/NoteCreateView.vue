<template>
    <div class="content mx-auto m-3" style="max-width: 500px;"> 
        <h1>Crear note</h1>
        <form>
            
  <div class="mb-3">
    <label for="name" class="form-label">Name</label>
    <input type="text" class="form-control" id="name" aria-describedby="emailHelp" v-model="note">
  </div>
  

  <button type="submit" class="btn btn-primary" v-on:click.prevent="sendNote">Submit</button>
</form>

<div class="alert alert-primary" role="alert">{{feedback}}</div>
    </div>
    </template>
    
<script lang="ts" setup>
import { Ref, ref } from "vue"
import useAuth from '@/store/auth'
import INote from "@/interfaces/INote"
import router from "@/router";

const store = useAuth()
const note = ref('')
const feedback = ref('')

const sendNote = async () => {
  feedback.value = "Procesando... Espera"
const response = await store.createNote(note.value)

if (response == false) {
  feedback.value = "Error al guardar Note"
} else {
  router.push({ name: 'list'})
}
}

  
</script>
    
    <style scoped>
    
    </style>