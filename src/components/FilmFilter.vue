<script setup>
    import {inject} from "vue";
    const sortType = inject("sortType");
    const changeSortType = (type) => {
        sortType.value = type;
    }
</script>



<template>
    <div class="film-filter">
        <small>Filter:</small>
        <button @click="changeSortType('release_date')" class="film-filter__button"
            :class="sortType === 'release_date' ? 'film-filter__button--active' : ''">Year</button>
        
        <button @click="changeSortType('title')" class="film-filter__button"
        :class="sortType === 'title' ? 'film-filter__button--active' : ''">Title</button>

        <button @click="changeSortType('running_time')" class="film-filter__button"
        :class="sortType === 'running_time' ? 'film-filter__button--active' : ''">Time</button>
    </div>
</template>




<style scoped>
    .film-filter {
        position: sticky;
        top: 0;
        display: flex;
        align-items: baseline;
        margin: -1rem -1rem 0 -1rem;
        padding: 0.5rem 1rem 0.5rem 1rem;
        gap: 0.5rem;
        background: white;
        box-shadow: 0 0.25rem 0.5rem hsla(0 0% 0% / 0.15);
        border-bottom-right-radius: 1rem;
        border-bottom-left-radius: 1rem;
        z-index: 100;
    }
    .film-filter__button {
        border: none;
        padding:0.5ch 1.5ch;
        border-radius:2ch;
        cursor: pointer;
    }
    .film-filter__button--active {
        /* box-shadow: 0 0 0.25rem hsla(0, 0%, 0%, 0.5) inset; */
        background: hsl(199, 39%, 52%);
        color: #fff;
    }
</style>