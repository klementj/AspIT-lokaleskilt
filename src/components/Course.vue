<script setup>

import { ref } from "vue";

const courses = [
  {
    title: 'Softwarekonstruktion 1',
    subtitle: 'Programming Introduction'
  },
  {
    title: 'Softwarekonstruktion 2',
    subtitle: 'Application Programming'
  },
  {
    title: 'Softwarekonstruktion 3',
    subtitle: 'Software Construction'
  },
  {
    title: 'Softwarekonstruktion 4.1',
    subtitle: 'Distributed Systems'
  },
  {
    title: 'Softwarekonstruktion 4.2',
    subtitle: 'Algorithms and Data Structures'
  },


  {
    title: 'Visualisering 1',
    subtitle: 'Web Introduction'
  },
  {
    title: 'Visualisering 2',
    subtitle: 'Web Construction'
  },
  {
    title: 'Visualisering 3.1',
    subtitle: 'Web Development'
  },
  {
    title: 'Visualisering 3.2',
    subtitle: 'Content Management'
  },
  

  {
    title: 'Teknik 1',
    subtitle: 'IT Introduction'
  },
  {
    title: 'Teknik 2',
    subtitle: 'IT Desktop, Server and Network'
  },
  {
    title: 'Teknik 3',
    subtitle: 'IT Support'
  },
  {
    title: 'Teknik 4.1',
    subtitle: 'Microsoft 365 Certified '
  },


  {
    title: 'Quality Assurance',
    subtitle: 'ISTQB Foundation certificering '
  },


  {
    title: 'AspIT Lab',
    subtitle: 'Foberedelse til praktik'
  }
]

const currentTitle = ref('')
const subtitle = ref('Undertitel til et fag')

function getSubtitle() {
  const result = courses.find( element => {
    return element.title === currentTitle.value
  })
  subtitle.value = result.subtitle
}

</script>


<template>
<section>
  <label for="fag" hidden>Fag</label>
  <input 
    list="fag" 
    type="text" 
    name="example" 
    placeholder="Fag, fx Teknik 1" 
    autocomplete="off" 
    id="title"

    v-model="currentTitle"
    @change="getSubtitle()"
  >

  <datalist id="fag">
    <option v-for="(course, index) in courses" :value="course.title" :key="index" >{{course.title}}</option>
  </datalist>

  <input 
    type="text" 
    :placeholder="subtitle" 
    id="subtitle"
  >
</section>
</template>


<style scoped>
section {
  margin-bottom: 1.5rem;
  position: relative;
  z-index: 1;
}

input {
  font-family: 'Sofia Regular';
  font-size: 3rem;
  color: #184440;
  position: relative;
  margin: 0;

}

input#title {
  width: calc(100% - 4px - 4px);
}

input#subtitle {
  width: calc(100% - 8px - 4px);
}

input#title:hover,
input#title:focus{
  z-index: 1;
}

input#subtitle {
  font-family: 'Sofia Ultra Light';
  font-size: 2rem;
  color: #28675b;
  padding: 4px; 
  margin-top: -.8rem;
}
</style>
