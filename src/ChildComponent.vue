<template>
  <div class="child">
    <slot name="header" />

    <p>
      <strong>Pesan:</strong> {{ message }}
    </p>
    <p>
      <strong>Penulis:</strong> {{ info.author }} | 
      <strong>Tanggal:</strong> {{ info.date }}
    </p>

    <slot />

    <slot name="footer" />

    <button @click="emitResponse">Kirim Balasan ke Induk</button>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
  message: {
    type: String,
    required: true
  },
  info: {
    type: Object,
    default: () => ({
      author: 'Tanpa Nama',
      date: 'Tidak Diketahui'
    })
  }
})

const emit = defineEmits(['response'])

function emitResponse() {
  emit('response', 'Halo dari komponen anak dengan slot bernama regi!')
}
</script>

<style scoped>
.child {
  border: 1px solid #ccc;
  padding: 15px;
  margin-top: 20px;
  background-color: #f0f8ff;
}
button {
  margin-top: 10px;
}
</style>
