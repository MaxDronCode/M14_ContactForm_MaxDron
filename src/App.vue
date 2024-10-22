<script setup>
import { reactive, ref, computed } from 'vue'
import ContactesForm from './components/ContactesForm.vue'

const telClass = ref('green')
let valorAFiltrar = ref('')

let llistaContactes = reactive([])
let contactesFiltrats = computed(() =>
  llistaContactes.filter(contacte =>
    contacte.nom.toLowerCase().includes(valorAFiltrar.value),
  ),
)

const gestionarRebuda = obj => {
  llistaContactes.push(obj)
}
</script>

<template>
  <header>
    <h1>Pràctica Contact Form</h1>
  </header>

  <main>
    <label for="form">Afegeix:</label><br />
    <ContactesForm @enviarDades="gestionarRebuda" /><br />
    <label for="filtra">Filtra:</label><br />
    <input type="text" v-model="valorAFiltrar" />
    <ul>
      <li v-for="contacte in contactesFiltrats" :key="contacte.tel">
        {{ contacte.nom }} - <span :class="telClass">{{ contacte.tel }}</span>
      </li>
    </ul>
  </main>
</template>

<style scoped>
.telClass {
  color: green;
}
</style>
