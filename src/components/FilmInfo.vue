<script setup>

    defineProps({
        // filmData: Object
        filmTime: String,
        filmTitle: String,
        filmTitleOriginal: String,
        filmDirector: String,
        filmYear: String,
        filmImage: String,
        filmDescription: String,
    });
    // console.log(props.filmData);
</script>

<template>
    <div class="film-info">

        <img :src="filmImage" class="film-info__image" />
        
        <div class="film-info__info">
            <h2>{{filmTitle}} <span class="film-info__year">{{filmYear}}</span></h2>
            <p> {{ filmTime }} </p>
            <p class="film-info__director">{{filmDirector}}</p>
            <p>{{filmDescription}}</p>
        </div>
    </div>
</template>

<style scoped>

.film-info {
    display: flex;
    position: sticky;
    top: 0;
    left: 0;
}
.film-info__image{
    height: 100vh;
    width: auto;
}
.film-info__info{
    padding: 1rem;
}
.film-info__director{
    font-style: italic;
}
.film-info__year {
    font-size: 65%;
    font-weight: normal;
    vertical-align: super;
    font-style: italic;
}
</style>