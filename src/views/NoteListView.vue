<template>
  <div class="content mx-auto m-3" style="max-width: 500px;"> 
    <h1>Note list</h1>
    <table class="table" v-if="notes.length > 0">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">Note</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="note in notes" :key="note.id">
      <th scope="row">{{ note.id }}</th>
      <td>{{ note.content }}</td>
    </tr>
    
  </tbody>
</table>
<p v-else>No data</p>
<router-link :to="{name: 'create'}">Ingresar note</router-link>
</div>
</template>

<script lang="ts" setup>
import useAuth from '@/store/auth'
import { ref, Ref, onMounted } from "vue";
import INote from '@/interfaces/INote'

const store = useAuth()

const notes:Ref<Array<INote>> = ref([])

  onMounted(async () => {
    notes.value = await store.getNotes()
  })



   
</script>

<style scoped>

</style>