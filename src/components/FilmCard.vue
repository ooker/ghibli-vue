<script setup>

defineProps({
  filmTitle: String,
  imageSrc: String
});

</script>

<template>
  <div class="film-card">
    <h3>{{ filmTitle }}</h3>
    <img :src="imageSrc" class="film-image" />
  </div>
</template>

<style>

  .film-card {
    padding: 1rem;
    box-shadow: 0 0.25rem 0.5rem hsla(0 0% 0% / 0.25);
    border-radius: 0.5rem;
    margin-bottom: 1rem;
  }

.film-image{
  width: 100%;
}
</style>