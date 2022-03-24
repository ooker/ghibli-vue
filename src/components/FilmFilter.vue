<script>
import {inject} from "vue";
export default {
    name: "Film Filter",
    setup(){
        const sortType = inject("sortType");
        const changeSortType = (type) => {
            sortType.value = type;
        }
        return {
            changeSortType,
            sortType
        }
    }
}
</script>

<template>
    <div class="film-filter">
        <small>Filter:</small>
        <button @click="changeSortType('year')" class="film-filter__button"
            :class="sortType === 'year' ? 'film-filter__button--active' : ''">Year</button>
        <button @click="changeSortType('title')" class="film-filter__button"
        :class="sortType === 'title' ? 'film-filter__button--active' : ''">Title</button>
    </div>
</template>



<style scoped>
    .film-filter {
        position: sticky;
        top: 1rem;
        display: flex;
        align-items: baseline;
        padding: 0.5rem 1rem 0.5rem 1rem;
        gap: 0.5rem;
        background: white;
        box-shadow: 0 0.25rem 0.5rem hsla(0 0% 0% / 0.15);
        border-radius: 9999px;
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
        background: hsl(0, 0%, 60%);
        color: #fff;
    }
</style>