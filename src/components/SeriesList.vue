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

<style scoped lang="scss">
    @import "../assets/style/variabili.scss";
    @import "../assets/style/generali.scss";

    h2 {
        font-size: 25px;
        margin-bottom: 30px;
        text-align: left;
    }

    ul {
        list-style: none;
        justify-content: center;
        padding-left: 0px;
    }

    img {
        width: 50px;
        height: 30px;
    }

</style>