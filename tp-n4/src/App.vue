<script setup lang="ts">
import TareasComponents from './components/TareasComponents.vue'
import ListaComponents from './components/ListaComponents.vue'
import DimensionComponents from './components/DimensionComponents.vue'
</script>

<template>
  <H1>Ciclos de Vida</H1>
  <component :is="TareasComponents"></component>
  <component :is="DimensionComponents"></component>
  <component :is="ListaComponents"></component>
  
  </template>

<style scoped>
h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
  background-color: rgb(81, 255, 0);
}
</style>
