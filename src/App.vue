<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import {ref} from "vue";
import HelloWorld from './components/HelloWorld.vue'
import FilmCard from './components/FilmCard.vue'

const filmsData = ref(null);

fetch('https://ghibliapi.herokuapp.com/films')
  .then(response => response.json())
    .then(data => filmsData.value = data)

//          .catch(console.error);

</script>


<template>
  


  <div v-for="(film, i) in filmsData" :key="'film'+i">
    <h2> {{ film.title }} </h2>
    <img :src="film.movie_banner" />
  </div>

  <FilmCard filmTitle="Mina olen film card" />

  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  
  <HelloWorld msg="See on minu message"  />

</template>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
