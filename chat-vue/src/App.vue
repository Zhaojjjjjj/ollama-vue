<script setup>
import { onMounted, ref } from 'vue'
import ollama from 'ollama'

let res = ref()

onMounted(async () => {
  await ollama
    .chat({
      model: 'llama3:8b',
      messages: [{ role: 'user', content: 'Why is the sky blue?' }],
    })
    .then((response) => {
      console.log(response)
      res.value = response.message.content
    })
})
</script>

<template>
  <div>
    <p v-html="res"></p>
  </div>
</template>

<style scoped></style>
