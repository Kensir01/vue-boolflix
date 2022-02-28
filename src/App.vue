<template>
  <div id="app">
    <MyHeader @search='getFilms' />
    <MyMain />
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

    }
  },
  methods: {
    getFilms(keyword) {

      console.log(keyword)


      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=9b07ec6dbfbbc8bbc8e1dc63c15c61b7&query=${keyword}&language=it-IT`)
      .then(function (response) {
        // handle success
        console.log(response);
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
