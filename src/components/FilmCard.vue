<script setup>

defineProps({
  filmTitle: String,
  imageSrc: String,
});

</script>

<template>
  <div class="film-card">
    <h3 class="film-card__title">{{ filmTitle }}</h3>
    <img :src="imageSrc" class="film-card__image" />
  </div>
</template>

<style>
  .film-card {
    padding: 1rem;
    box-shadow: 0 0.25rem 0.5rem hsla(0 0% 0% / 0.25);
    border-radius: 0.5rem;
    margin-bottom: 1rem;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
  }
  .film-card:hover {
    background: hsl(300, 94%, 87%);
    transition: all 0.3s ease-in-out;
  }
  .film-card__title {
    margin-top: 0;
  }
  .film-card__image{
    width: 100%;
  }
</style>