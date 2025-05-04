<template>
    <div>
      <h2>Lista de Profesiones</h2>
      <ul v-if="items.length > 0">
        <li v-for="(item, index) in items" :key="item.id">
          <strong>{{ item.nombre }}</strong>: {{ item.descripcion }}
        </li>
      </ul>
      <p v-else>Cargando profesiones...
<i class="pi pi-spin pi-cog"></i>
      </p>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  import { profesiones } from '../resource/profesiones'; 
  import 'primeicons/primeicons.css'; //
  
  export default {
    name: 'Lista',
    setup() {
      const items = ref([]);
  
      onMounted(() => {
             setTimeout(() => {
          items.value = profesiones; 
        }, 3000); // 3 segundos de espera
      });
  
      return {
        items,
      };
    },
  };
  </script>
  
  <style scoped>
  h2 {
    font-size: 1.5em;
    margin-bottom: 10px;
  }
  
  ul {
    list-style-type: none;
    padding: 0;
  }
  
  li {
    background: #f4f4f4;
    margin: 5px 0;
    padding: 10px;
    border-radius: 5px;
  }
  
  p {
    font-style: italic;
    color: #888;
  }
  </style>