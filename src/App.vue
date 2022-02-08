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
      .catch(console.error);

</script>


<template>
  
  <main class="films">

    <nav class="films-list">
      <film-card v-for="(film, i) in filmsData" :key="'film'+i"
    :filmTitle="film.title" :imageSrc="film.movie_banner" />
    </nav>

    <section class="film-info">

    </section>
  </main>

  



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

.films{
  display: flex;
}
.films-list{
  flex: 0 0 30%;
}

</style>
