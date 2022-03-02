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

      <div>{{info.vote_average}}</div>

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
    methods: {
        getTitle () {
            if (this.info.title) {
                return this.info.title;
            } else {
                return this.info.name;
            }
        }
    }
}
</script>

<style>

</style>