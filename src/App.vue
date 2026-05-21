<script setup>
import { ref } from "vue";

const plantName = ref("");
const plants = ref([]);

function addPlant() {
  plants.value.push(plantName.value);
  plantName.value = "";
}
</script>

<template>
  <h1>Plant tracker</h1>
  <input v-model="plantName" placeholder="Enter plant name" />
  <button @click="addPlant()">Add plant</button>
  <ul>
    <li v-for="plant in plants" :key="plant">{{ plant }}</li>
  </ul>
</template>
