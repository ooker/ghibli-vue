<script setup>

    defineProps({
        // filmData: Object
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

        <!-- <img :src="filmData.image" />
        
        <div>
            <h1>{{filmData.title}} {{filmData.release_year}}</h1>
            <p class="film-info__director">{{filmData.director}}</p>
            <p>{{filmData.description}}</p>
        </div> -->

        <img :src="filmImage" class="film-info__image" />
        
        <div class="film-info__info">
            <h2>{{filmTitle}} {{filmYear}}</h2>
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

</style>