<template>
    <ul>
        <FilmCard v-for="(film, index) in films" :key="index" :film='film' />
    </ul>
</template>

<script>

import FilmCard from './partials/FilmCard.vue'

export default {
    name: "FilmList",
    props: {
        'films': Array
    },
    components: {
        FilmCard
    }
}
</script>

<style>

</style>