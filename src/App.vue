<template>
  <div id="app">
    <MyHeader @search='getFilms' />
    <MyMain :films="films"/>
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
      api_key: '9b07ec6dbfbbc8bbc8e1dc63c15c61b7',
      language: 'it-IT'
    }
  },
  methods: {
    getFilms(keyword) {

      const params ={
        params: {
          'api_key': this.api_key,
          'query': keyword,
          'language' : this.language
        }
      };


      axios.get('https://api.themoviedb.org/3/search/movie/', params )
      .then((response) => {
        this.films = response.data.results;
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
      .then(function () {
        // always executed
      });
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
