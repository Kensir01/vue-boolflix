<template>
    <main>
        <div class="container">
            <FilmList :films='films'/>
            <SeriesList :series='series'/>
        </div>
    </main>
</template>

<script>

    import FilmList from './FilmList.vue';
    import SeriesList from './SeriesList.vue';
    
    export default {
    name: 'MyMain',
    props: {
        'films': Array,
        'series': Array

    },
    components: {
        FilmList,
        SeriesList
    }
}
</script>
<style scoped lang="scss">

    @import "../assets/style/variabili.scss";

    ul {
        padding-top: 20px;
    }

</style>