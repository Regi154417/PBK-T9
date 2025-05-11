<template>
  <div class="app">
    <h1>Komponen Induk</h1>

    <ChildComponent 
      :message="parentMessage" 
      :info="{ author: 'Vue Mastery', date: '11 Mei 2025' }"
      @response="handleChildResponse"
    >
      <template #header>
        <h2>Ini adalah slot header dari induk</h2>
      </template>

      <template #default>
        <p>Ini adalah isi slot default dari induk.</p>
      </template>

      <template #footer>
        <small>Ini adalah slot footer dari induk.</small>
      </template>
    </ChildComponent>

    <p v-if="childResponse">{{ childResponse }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import ChildComponent from './ChildComponent.vue'

const parentMessage = ref('Pesan dari Komponen Induk')
const childResponse = ref('')

function handleChildResponse(msg) {
  childResponse.value = msg
}
</script>

<style scoped>
.app {
  padding: 20px;
  font-family: sans-serif;
}
</style>
