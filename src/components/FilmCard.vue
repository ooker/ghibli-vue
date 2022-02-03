<script setup>
import { ref } from 'vue'
defineProps({
  filmTitle: String,
  filmImage: String,
})
const count = ref(0)
</script>

<template>
    <div>
      <h2>{{filmTitle}}</h2>
      <img :src="filmImage" />
    </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
