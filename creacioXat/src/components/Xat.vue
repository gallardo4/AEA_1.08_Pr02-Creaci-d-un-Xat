<script setup>
import { ref } from 'vue';
import Missatge from './Missatge.vue';

// Llista de missatges que es mostrarà al component pare
const missatges = ref([]);

// Funció per afegir un nou missatge a la llista
const afegirMissatge = (missatge) => {
  missatges.value.push(missatge);
};
</script>

<template>
  <div class="xat-container">
    <h2>Xat entre usuaris</h2>
    <ul class="missatges">
        <li v-for="(msg, index) in missatges" :key="index">
            <p>Usuari 1: {{ msg }}</p>
        </li>
    </ul>
    <!-- Passar la funció d'afegir missatge com a prop -->
    <Missatge @enviarMissatge="afegirMissatge" autor="Usuari 1" />
  </div>
</template>