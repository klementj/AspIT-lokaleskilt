<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
// import { ref } from "vue";
// import CourseSign from './components/template/CourseSign.vue'
// import Navigation from "./components/Navigation.vue";
// import SimpleSign from "./components/template/SimpleSign.vue";
// import ImageUpload from "./components/ImageUpload.vue";


function print() {
  //Valideing af inputs - Nice to have

  // Save inputs to local stoage fist - Nice to have
  window.print();
}

</script>

<template>

<div class="container">
  <!-- <ImageUpload /> -->
  <!-- Navigation -->
  <!-- <Navigation /> -->
  <nav>
    <router-link to="/klasseskilt">Klasseskilt</router-link>
    <router-link to="/lokaleskilt">Andre døre</router-link>
  </nav>

  <!-- Template -->
  <div class="template">
    <router-view />
    <!-- <CourseSign /> -->
    <!-- <SimpleSign /> -->
  </div>

  <!-- Print button -->
  <a href="#" class="button" @click.prevent="print()"><svg fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z"></path></svg>Print</a>
</div>


</template>

<style>
@font-face {
  font-family: 'Sofia Regular';
  src: local('Sofia Pro Regular'), 
       url('../src/assets/fonts/Sofia_Pro_Regular.otf') format('opentype');
}
@font-face {
  font-family: 'Sofia Light';
  src: local('Sofia Pro Light'), 
       url('../src/assets/fonts/Sofia_Pro_Light.otf') format('opentype');
}
@font-face {
    font-family: 'Sofia Ultra Light';
    src: local('Sofia Pro Light'), 
         url('../src/assets/fonts/Sofia_Pro_Ultra_Light.otf') format('opentype');
}

@page {
  size: A4 portrait;
  margin: 6mm 12mm 0 12mm;
}

*, ::before, ::after {
  box-sizing: border-box;
}

body {
  --primary-color: hsl(177, 69%, 15%);
  --secondary-color: hsl(9, 86%, 60%);

  font-family: 'Sofia Regular', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  background-color: #FF3CAC;
  background-image: linear-gradient(225deg, #FF3CAC 0%, #784BA0 50%, #2B86C5 100%);

  height: 100vh;
  margin: 0;
}


.container {
  display: flex;
  gap: 2rem;
  flex-direction: column;
  max-width: calc(210mm + 12mm);
  margin: 0 auto;
}



/* Colors */
.a5-color-light {
 background-color: white;
}

.a5-color-dark {
  background-color: var(--primary-color);
}

/* Orientation and size */
.a5-size-portrait {
  position: relative;
  width: 210mm;
  height: 148mm;
}

.a5-size-landscape {
  width: 210mm;
  height: 148mm;
}

@media screen {
  .a5-size-portrait,
  .a5-size-landscape{
    height: 148mm;
    width: 100%;
    padding: 6mm 12mm;
  }
}

@media print {
  .a5-size-portrait,
  .a5-size-landscape {
    height: 142mm;
    width: 186mm;
  }

  .a5-size-portrait {
    border-bottom: 2px dotted hsl(0, 0%, 50%);
  }
}





@media screen {
  .container {
    padding: 1rem;
  }
}

.container > .button {
  align-self: flex-end;
}

input{
  border-color: transparent;
  transition: all 100ms ease-out;
  margin-bottom: .5rem;
  width: 100%;
  background-color: transparent;
  padding-top: 0;
  padding-bottom: 0;
}

input:hover{
  background-color: #ececec;
}

/* input:focus{
  background-color: black;
} */


.button {
  display: inline-flex;
  gap: .5em;
  align-items: center;
  background-color: #fff;
  color: black;
  padding: 1rem 2rem;
  text-decoration: none;
  transition: all 50ms ease-out;
}

.button:hover,
.button:focus {
  background-color: var(--secondary-color);
  /* color: white; */
}

.button > svg {
  width: 20px;
}

@media print {
  body{
    background-color: white;
    background-image: none;
  }

  .navigation,
  nav,
  form,
  .button{
    display: none;
    
  }
}
</style>
