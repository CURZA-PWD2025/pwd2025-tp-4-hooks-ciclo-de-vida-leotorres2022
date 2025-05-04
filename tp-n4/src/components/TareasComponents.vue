
<template>
    <div>
      <h1>Lista de Tareas</h1>
      <ul>
        <li
          v-for="(tarea, index) in tareas"
          :key="index"
          :class="{ antiguo: index < cantidadAnterior }"
        >
          {{ tarea }}
        </li>
      </ul>
      <input
        v-model="nuevaTarea"
        type="text"
        placeholder="Escribe una nueva tarea"
      />
      <button @click="agregarTarea">Agregar Tarea</button>
    </div>
  </template>
  
  <script setup lenguage="ts">
  import { ref, onBeforeUpdate, onUpdated } from 'vue';
  
  // Lista de tareas inicial
  const tareas = ref([]);
  const nuevaTarea = ref('');
  const cantidadAnterior = ref(0); 

  // Función para agregar una nueva tarea
  const agregarTarea = () => {
    if (nuevaTarea.value.trim() !== '') {
      tareas.value.push(nuevaTarea.value.trim());
      nuevaTarea.value = '';
    }
  };
  
  // Hook que se ejecuta antes de que el DOM se actualice
  onBeforeUpdate(() => {
    console.log('Lista aún no modificada');
    cantidadAnterior.value = tareas.value.length; // Guardar la cantidad actual de tareas
  });
  
  // Hook que se ejecuta después de que el DOM se actualice
  onUpdated(() => {
    console.log('Lista modificada');
  });
  </script>
  
  
  
  <style scoped>
  h1 {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    margin: 0.5rem 0;
  }
  
  li.antiguo {
    color: green; /*color de la lista anterior*/
    font-weight: bold;
  }
  
  input {
    margin-right: 0.5rem;
    padding: 0.5rem;
  }
  
  button {
    padding: 0.5rem 1rem;
    cursor: pointer;
  }
  </style>