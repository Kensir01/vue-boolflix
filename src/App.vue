<template>
  <div id="app">

    <MyHeader @search='doSearch' />
    <MyMain :films="films" :series="series" />
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'

const axios = require('axios');

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data() {
    return{
      films: [],
      series: [],
      results: [],
      api_key: '9b07ec6dbfbbc8bbc8e1dc63c15c61b7',
      language: 'it-IT'
    }
  },
  methods: {

    doSearch(keyword) {
      
      const parametri ={
        params: {
          'api_key': this.api_key,
          'query': keyword,
          'language' : this.language
        }
      };

      this.getFilms(parametri);
      this.getTv(parametri);


    },

    getFilms(params) {

      axios.get('https://api.themoviedb.org/3/search/movie/', params )
      .then((response) => {
        this.films = response.data.results;
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
    },
    
    getTv(params) {

      axios.get('https://api.themoviedb.org/3/search/tv/', params )
      .then((response) => {
        this.series = response.data.results;

      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
    }
  }
}
</script>

<style lang="scss">
// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
