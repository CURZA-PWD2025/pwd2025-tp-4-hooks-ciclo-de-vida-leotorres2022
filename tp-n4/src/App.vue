<script setup lang="ts">
import TareasComponents from './components/TareasComponents.vue';
import ListaComponents from './components/ListaComponents.vue';
import DimensionComponents from './components/DimensionComponents.vue'
import { ref } from 'vue';
// Lista de componentes
const componentsList = [
  { name: 'Tareas', component: TareasComponents },
  { name: 'Dimension', component: DimensionComponents },
  { name: 'Lista Profesiones', component: ListaComponents },
];

// Variable reactiva para el componente seleccionado

const seleccionComponente = ref(componentsList[0].component);
</script>

<template>
  <H1>Ciclos de Vida</H1> 
  <select v-model="seleccionComponente">  
    <option v-for="(comp, index) in componentsList" :key="index" :value="comp.component">
      {{ comp.name }}
    </option>
  </select>
     <component :is="seleccionComponente" />
  </template>

<style scoped>
h1 {
  font-size: 2rem; 
  margin-bottom: 1rem;
  background-color: rgb(81, 255, 0);
}
</style>
