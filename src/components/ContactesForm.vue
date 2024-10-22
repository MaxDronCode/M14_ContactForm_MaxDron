<script setup>
import { ref } from 'vue'
let nom = ref('')
let tel = ref('')
const emit = defineEmits(['enviarDades'])
const enviarDades = () => {
  if (nom.value && tel.value){

    emit('enviarDades', {nom : nom.value, tel : tel.value})
  }
}
</script>
<template>
  <input type="text" placeholder="Nom del contacte" v-model="nom">
  <input type="text" placeholder="Número de telèfon" v-model=tel>
  <button value="Afegir contacte" @click="enviarDades">Afegir Contacte</button>

</template>
<style scoped></style>