<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import {ref, provide, computed} from "vue";
import FilmCard from './components/FilmCard.vue';
import FilmInfo from './components/FilmInfo.vue';
import FilmFilter from './components/FilmFilter.vue';

const filmsData = ref(null);
const activeFilm = ref(0);
const sortType = ref("null");

fetch('https://ghibliapi.herokuapp.com/films')
  .then(response => response.json())
    .then(data => {
      filmsData.value = data;
      sortType.value = "title";
    })
    .catch(console.error);


const filmCardClick = (i) => {
  activeFilm.value = i;
}

const sortedData = computed(() => {
  switch (sortType.value){
    case "year":
      return [...filmsData.value].sort( (a, b) => {
        return a.release_date.localeCompare(b.release_date);
      });
    case "title":
      return [...filmsData.value].sort( (a, b) => {
        return a.title.localeCompare(b.title);
    });
  } 
});

provide("sortType", sortType);
provide("activeFilm", activeFilm);

</script>


<template>
  
  <main class="films">

    <nav class="films-list">
      
      <film-filter />

      <film-card v-for="(film, i) in sortedData" :key="'film'+i"
        :filmTitle="film.title" 
        :imageSrc="film.movie_banner" 
        @click="filmCardClick(i)"
     />
    
    </nav>

    <section>

      <!-- <film-info v-if="filmsData"
        :filmData="filmsData[activeFilm]"
      /> -->
      <film-info v-if="sortedData"
        :filmTitle="sortedData[activeFilm].title"
        :filmImage="sortedData[activeFilm].image"
        :filmDescription="sortedData[activeFilm].description"
        :filmYear="sortedData[activeFilm].release_date"
        :filmDirector="sortedData[activeFilm].director"
      />
      <!-- 
        <div v-else>Loading...</div> 
      -->

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
  display: grid;
  grid-template-columns: 1fr;
  gap: 0.5rem;
}

@media (min-width: 1024px) {
  .films-list{
    grid-template-columns: 1fr 1fr;
  }
} 

</style>
