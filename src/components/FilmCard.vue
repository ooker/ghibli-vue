<script setup>

defineProps({
  filmTitle: String,
  imageSrc: String,
});

</script>

<template>
  <div class="film-card">
    <h4 class="film-card__title">{{ filmTitle }}</h4>
    <img :src="imageSrc" class="film-card__image" />
  </div>
</template>

<style>
  .film-card {
    padding: 0.75rem;
    box-shadow: 0 0.125rem 0.25rem hsla(0 0% 0% / 0.2);
    border-radius: 0.25rem;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
  }
  .film-card:hover {
    background: hsl(51, 89%, 93%);
    box-shadow: 0 0.25rem 0.5rem hsla(0 0% 0% / 0.2);
    transform: translateY(-0.3rem);
    transition: all 0.3s ease-in-out;
  }
  .film-card__title {
    margin: 0 0 0.5rem 0;
  }
  .film-card__image{
    width: 100%;
  }
</style>