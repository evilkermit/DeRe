<template>
  <ul>
    <li v-for="rva in rva_list" :key="rva.name">
      <router-link :to="`/viewer?rva=${rva.name}`">
        <img :src="rva.preview" />
      </router-link>
    </li>
  </ul>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const rva_list = ref([])
const location = ref('')

onMounted(() => {
  location.value = window.location.hostname

  fetch(`//${location.value}:5577/rva`)
    .then((response) => response.json())
    .then((data) => {
      data.forEach((item) => {
        item.preview = `//${location.value}:5577${item.preview}`
        rva_list.value.push(item)
      })
    })
})
</script>

<style scoped>
ul {
  display: grid;
  grid-template-columns: repeat(5, calc(20% - 0.8em));
  gap: 1em;
  list-style: none;
  padding: 2em;
}

li img {
  width: 100%;
}
</style>
