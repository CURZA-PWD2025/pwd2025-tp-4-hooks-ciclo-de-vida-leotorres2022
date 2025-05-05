<template>

    <div>
    <h1>Dimensiones del Componente</h1>
    <p>Ancho: {{ width }} px</p>
    <p>Alto: {{ height }} px</p>
  </div>

</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const width = ref(window.innerWidth);
const height = ref(window.innerHeight);

// Función para actualizar las dimensiones
const actualizarDimensiones = () => {
  width.value = window.innerWidth;
  height.value = window.innerHeight;
};

// Hook que se ejecuta cuando el componente se monta
onMounted(() => {

  window.addEventListener('resize', actualizarDimensiones);
});

// Hook que se ejecuta cuando el componente se desmonta
onUnmounted(() => {
  window.removeEventListener('resize', actualizarDimensiones);
});
</script>

<style scoped>
h1 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

p {
  font-size: 1rem;
  margin: 0.5rem 0;
}
</style>

