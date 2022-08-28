<script setup>
import { ref } from "vue";

const teachers = [
  {
    id: 'jaje',
    name: 'Jan Jeppesen'
  },
  {
    id: 'kljo',
    name: 'Klement Johansen'
  },
  {
    id: 'paho',
    name: 'Patrick Holst'
  },
  {
    id: 'stla',
    name: 'Steen Larsen'
  },
  {
    id: 'siso',
    name: 'Sidsel Sørensen'
  },
  {
    id: 'kaod',
    name: 'Sanne Odgaard'
  },
  {
    id: 'stsv',
    name: 'Stine Svendsen'
  },
  {
    id: 'jema',
    name: 'Jesper Torstensson'
  }
]

const emit = defineEmits(['change-image'])
const selectedTeacher = ref(null) 

function findTeacherImage() {
  if (selectedTeacher.value === "") {
    emit('change-image', "placeholder")
    return
  }

  const result = teachers.find( teacher => {
    return teacher.name === selectedTeacher.value
  })

  emit('change-image', result.id)

}

</script>


<template>
  <label for="teachers" hidden>Lærer</label>
    <input
      list="teachers" 
      type="text" 
      name="teachers" 
      placeholder="Vælg en lærer eller indtast din egen, fx Julamanden" 
      autocomplete="off" 

      v-model="selectedTeacher"
      @change="findTeacherImage()"
    >

  <datalist id="teachers">
    <option v-for="teacher in teachers" :value="teacher.name" :key="teacher.id" >{{teacher.name}}</option>
  </datalist>
</template>


<style scoped>
input {
  font-family: 'Sofia Regular';
  font-size: 1.2rem;
  color: #184440;
}

p {
  font-family: 'Sofia Ultra Light';
  font-size: 2rem;
  color: #28675b;
  padding: 4px;
  margin: 0;
  margin-top: -0.8rem;
}
</style>
