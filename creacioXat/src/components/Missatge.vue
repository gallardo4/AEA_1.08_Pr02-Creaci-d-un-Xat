<script setup>
import { ref, defineEmits } from 'vue';

// Definir els props
const props = defineProps({
  author: String
});

// Definir l'emissor d'events
const emit = defineEmits();

// Variable per emmagatzemar el missatge que l'usuari escriu
const missatge = ref('');

// Funció per enviar el missatge al component pare
const enviarMissatge = () => {
  if (missatge.value.trim()) {
    // Emitir l'event al component pare
    emit('enviarMissatge', {author: props.author, text: missatge.value});
    missatge.value = ''; // Netejar el camp de text després d'enviar
  }
};
</script>

<template>
  <form @submit.prevent="enviarMissatge" class="missatge-form">
    <input type="text" v-model="missatge" placeholder="Escriu el teu missatge" required />
    <button type="submit">Enviar</button>
  </form>
</template>