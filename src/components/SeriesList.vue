<template>
    <section>
        <h1>Elenco delle serie</h1>
        <ul>
            <MyCard v-for="(serie, index) in series" :key="index" :info='serie' />
        </ul>
    </section>
</template>

<script>

import MyCard from './partials/MyCard.vue'

export default {
    name: "SerieList",
    props: {
        'series': Array
    },
    components: {
        MyCard
    }
}
</script>

<style>

</style>