<script setup>
import { ref } from "vue";

const lokaler = ['Lokale U1', 'Lokale U2', 'Lokale U3', 'Lokale U4', 'Lokale U5', 'Lokale U6']
const personale = {

}

function print(text) {
  console.error(text);
}

</script>

<template>

  <label for="lokale">Vælg eller skriv et lokale <br>
  <input @focus="print(selected)" v-model="selected" type="text" name="example" list="lokale" placeholder="Lokale U1" autocomplete="off" autofocus>
  </label>
  <datalist id="lokale">
    <option v-for="(lokale, index) in lokaler" :value="lokale" :key="index"/>
  </datalist>

  <a href="#" @click="print('Fra knap')">hej</a>
</template>



<style scoped>

</style>
