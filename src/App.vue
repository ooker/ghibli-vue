<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import {ref} from "vue";
import FilmCard from './components/FilmCard.vue';
import FilmInfo from './components/FilmInfo.vue';

const filmsData = ref(null);
const activeFilm = ref(0);


fetch('https://ghibliapi.herokuapp.com/films')
  .then(response => response.json())
    .then(data => filmsData.value = data)
      .catch(console.error);


const filmCardClick = (i) => {
  activeFilm.value = i;
}

</script>


<template>
  
  <main class="films">

    <nav class="films-list">
      
      <film-card v-for="(film, i) in filmsData" :key="'film'+i"
        :filmTitle="film.title" 
        :imageSrc="film.movie_banner" 
        @click="filmCardClick(i)" />
    
    </nav>

    <section>

      <!-- <film-info v-if="filmsData"
        :filmData="filmsData[activeFilm]"
      /> -->
      <film-info v-if="filmsData"
        :filmTitle="filmsData[activeFilm].title"
        :filmImage="filmsData[activeFilm].image"
        :filmDescription="filmsData[activeFilm].description"
        :filmYear="filmsData[activeFilm].release_date"
        :filmDirector="filmsData[activeFilm].director"
      />
      <!-- <div v-else>Loading...</div> -->

    </section>
  </main>

  



</template>



<style>
body{
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

.films{
  display: flex;
}
.films-list{
  flex: 0 0 30%;
  padding: 1rem;
}

</style>
