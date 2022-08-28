<script setup>
import Activity from '../Course.vue';
import Header from '../Header.vue';

</script>


<template>
  <div class="a5-size-landscape a5-color-dark">

    <Header />

    <main>
      <Activity />
    </main>

  </div>
</template>


<style>
/* .a5-landscape{
  --page-size: A4 landscape;
} */

/* @page cannot be scoped. Last component in route overwrites 
solutions: 
  1. Make router load different css.
     https://laracasts.com/discuss/channels/vue/change-the-css-of-the-page-in-vue-spa-project-with-vue-route
  2. In component create style with JavaScript. Similar to this
     https://stackoverflow.com/a/53291660
*/

/* @page {
  size: A4 portrait;
  margin: 6mm 12mm 0 12mm;
} */

.a5-landscape {
  background-color: var(--primary-color);
  width: 210mm;
  height: 148mm;
}


main {
    display: flex;
    justify-content:space-between;
}







.teachimg {
    margin-top: 22px;
    margin-bottom: -3px;
    margin-right: 50px;
    object-fit:cover;
    height: 300px;
}
ul {
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
}
</style>
