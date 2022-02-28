<template>
    <main>
        <FilmList :films='films'/>
    </main>
</template>

<script>

    import FilmList from './FilmList.vue';

    export default {
    name: 'MyMain',
    props: {
        'films': Array
    },
    components: {
        FilmList
    }
}
</script>

<style>

</style>