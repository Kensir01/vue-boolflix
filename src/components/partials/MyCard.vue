<template>
  <li>
    <div>{{getTitle()}}</div>
    <div>{{info.original_title}}</div>

    <img v-if="info.poster_path" :src="`https://image.tmdb.org/t/p/w342/${info.poster_path}`">
    <img v-else :src="require('../../assets/img/no_pic.jpg')">

    <div>
        <img v-if="languages.includes(info.original_language)" :src="require('../../assets/flags/'+ info.original_language + '.webp')" >
        <span v-else>{{info.original_language}}</span>
    </div>
    
    <div>
        <i v-for="i in 5" :key="i" class="fa-star" :class="(i < getComputedStar)?'fa-solid':'fa-regular'"></i>
    </div>

  </li>
</template>

<script>
export default {
    name: 'MyCard',
    props: {
        'info': Object
    },
    data () {
        return {
            languages: ['en','it'],
        }
    },
    computed: {
        getComputedStar() {
            return Math.ceil(this.info.vote_average /2);
        }
    },
    methods: {
        getTitle () {
            if (this.info.title) {
                return this.info.title;
            } else {
                return this.info.name;
            }
        },
    }
}
</script>

<style>

</style>