<script setup>
import { ref } from 'vue';
import Missatge from './Missatge.vue';

// Llista de missatges que es mostrarà al component pare
const missatges = ref([]);
const author = 'Usuari 1';

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
            <span>{{ msg.author }}:</span> {{ msg.text }}
        </li>
    </ul>
    <!-- Passar la funció d'afegir missatge com a prop -->
    <Missatge @enviarMissatge="afegirMissatge" :author="author" />
  </div>
</template>