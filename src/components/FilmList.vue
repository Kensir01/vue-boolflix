<template>
    <section>
        <h1>Elenco dei film</h1>
        <ul>
            <MyCard v-for="(film, index) in films" :key="index" :info='film' />
        </ul>
    </section>

</template>

<script>

import MyCard from './partials/MyCard.vue'

export default {
    name: "FilmList",
    props: {
        'films': Array
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