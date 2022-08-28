<script setup>

const rooms = ['Lokale U1', 'Lokale U2', 'Lokale U3', 'Lokale U4', 'Lokale U5', 'Lokale U6', 'Lokale M1', 'Lokale M2', 'Lokale M3', 'Lokale M4', 'Lokale M5', 'Lokale M6']

</script>


<template>
  <header>

    <label for="lokale" hidden>Lokale</label>
    <input 
      list="lokale" 
      type="text" 
      name="lokale" 
      placeholder="Lokalets navn, fx Lokale M2 eller S212" 
      autocomplete="off" 
      autofocus="true"
    >
    <datalist id="lokale">
      <option v-for="room in rooms" :value="room">{{room}}</option>
    </datalist>

    <div class="image">
        <img class="logo" alt="AspIT" src="../assets/logo.svg">
    </div>
  </header>
  
</template>


<style scoped>

input {
  font-family: 'Sofia Light';
  font-size: 2rem;
  color: #28675b;
  flex-grow: 1;
}

header {
  display: flex;
  gap: 1rem;
  justify-content: space-between;
  align-items: flex-start;
  position: relative;
  z-index: 1;
  margin-bottom: 2rem;
}
.logo {
    width: 72px;
}
</style>
