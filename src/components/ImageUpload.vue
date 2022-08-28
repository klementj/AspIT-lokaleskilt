<script setup>
// https://developer.mozilla.org/en-US/docs/Web/API/File/Using_files_from_web_applications#Example%3a_Using_object_URLs_to_display_images
const URL = window.URL || window.webkitURL

const props = defineProps({
  data: {
    type: Object,
    default: () => ({})
  }
})

function read(files) {
  return new Promise((resolve, reject) => {
    if (!files || files.length === 0) {
      resolve()
      return
    }

    const file = files[0]

    if (/^image\/\w+$/.test(file.type)) {
      if (URL) {
        resolve({
          loaded: true,
          name: file.name,
          type: file.type,
          url: URL.createObjectURL(file)
        })
      } else {
        reject(new Error('Skift til en nyere browser'))
      }
    } else {
      reject(new Error('Vælg venligst et billede'))
    }
  })
}

function change({target}) {
  read(target.files)
    .then( data => {
      target.value = ''
      update(data)
    })
    .catch( error => {
      target.value = ''
      alert(error)
    })
}

function dragover(event) {
  event.preventDefault()
}

function drop(event) {
  // event.preventDefault()
  read(event.dataTransfer.files).catch(alert)
}

function alert(event) {
  window.alert(event && event.message ? event.message : event)
}

function update(data) {
  console.log(data);
  Object.assign(props.data, data)
}


</script>


<template>
  <div class="loader" @change="change" @dragover.prevent="dragover" @drop.prevent="drop">
    <p>Træk billede hertil eller 
      <label for="file" class="browse">browse...
        <input id="file" class="sr-only" type="file" accept="image/*">
      </label>
    </p>
  </div>

  <img :src="props.data.url" alt="">
</template>


<style scoped>
.loader {
  display: table;
  height: 0;
  overflow: hidden;
  width: 100%;
  min-height: 400px;
  /* background: white; */
  border: 1px dotted #e0e0e0;
}

.loader > p {
  color: #999;
  display: table-cell;
  text-align: center;
  vertical-align: middle;
}
</style>