<script setup>
import { ref } from "vue";

const plantName = ref("");
const plants = ref([]);

function addPlant() {
  plants.value.push(plantName.value);
  plantName.value = "";
  localStorage.setItem("plants", JSON.stringify(plants.value));
}

function removePlant(index) {
  plants.value.splice(index, 1);
  localStorage.setItem("plants", JSON.stringify(plants.value));
}

const saved = localStorage.getItem("plants");
if (saved) {
  plants.value = JSON.parse(saved);
}
</script>

<template>
  <h1>Plant tracker</h1>
  <input v-model="plantName" placeholder="Enter plant name" />
  <button @click="addPlant()">Add plant</button>
  <ul>
    <li v-for="(plant, index) in plants" :key="plant">
      {{ plant }}
      <button @click="removePlant(index)">x</button>
    </li>
  </ul>
</template>
