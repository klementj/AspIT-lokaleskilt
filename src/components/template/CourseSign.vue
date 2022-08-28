<script setup>
import Header from '../Header.vue';
import Course from '../Course.vue';
import Teacher from '../Teacher.vue';
import Students from '../Students.vue';

import { computed, ref } from "vue";

const teacherID = ref('placeholder')
const teacherImage = computed(() => `/src/assets/${teacherID.value}.jpg`)

function changeTeacherImage(id) {
  teacherID.value = id
}

let myRules = document.styleSheets[0].cssRules;
console.log(myRules[0])

</script>


<template>
<div class="a5-size-portrait a5-color-light">

    <Header />

    <Course />

    <main class="classinfo">
      

      <div class="inclass">
        <Teacher 
          @change-image="changeTeacherImage"
        />
        <Students />
        <Students />
        <Students />
        <Students />
        <Students />
        <Students />
        <Students />
        <Students />
        <Students />
          <!-- <ul>
            <li class="teacher">teacher</li>
            <li class="student">Mads Nørgaard</li>
            <li class="student">Natascha Bjerning</li>
            <li class="student">Simon Mortensen</li>
            <li class="student">Xiao-Di Lin</li>
            <li class="student"></li>
            <li class="student"></li>
            <li class="student"></li>
            <li class="student"></li>
            <li class="student"></li>
          </ul> -->
      </div>
      <div class="photo">
        <img class="teachimg" alt="Lærer" :src="teacherImage">
      </div>
    </main>

  </div>

</template>


<style>
/* .a5-portrait{
  --page-size: A4 portrait;
} */

/* @page {
  size: A4 landscape;
  margin: 6mm 12mm 0 12mm;
} */


.photo {
  width: 310px;
  position: absolute;
  overflow: hidden;
  z-index: 0;
  right: 0;
  bottom: 0;
}

.teachimg {
    object-fit:cover;
    width: 100%;
    display: block;
    transform: scale(1.2)
}

@media print {
  .a5-portrait {
    height: 142mm;
    width: 186mm;
    border-bottom: 2px dotted hsl(0, 0%, 50%);
  }
}


main {
    display: flex;
    justify-content:space-between;
}



/* ul {
    list-style-type: none;
    font-family: 'Sofia Light', sans-serif;
    font-size: 1.2rem;
    margin-bottom: 0;
    margin-top: 50px;
    color: #184440;
}
ul > .teacher {
    font-family: 'Sofia Regular';
    margin-bottom: 10px;
    margin-top: -10px;
}
li {
    margin:0;
}
li:empty {
    display: none;
}
hr {
    border: 1px dotted lightgrey;
    margin:0;
} */
</style>
