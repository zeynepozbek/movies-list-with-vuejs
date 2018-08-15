<template>
  <div id="app" class="container mx-auto pt-4">
    <!--<img alt="Vue logo" src="./assets/logo.png">-->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <search v-on:SearchRequested = "handleSearch"></search>
    <p v-if="isLoading">Loading...</p>
    <preview :movies=movies></preview>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search.vue'
import Preview from './components/Preview.vue'


export default {
  name: 'app',

  components: {
    HelloWorld,
    Search,
    Preview
  },
  data() {
    return {
        isLoading: true,
        movies: []
    }
  },
  methods: {
   doQuery(url){
       fetch(url)
           .then((res) => { return res.json() })
           .then((res) => {
               this.movies = res.results;
               //console.log(res.results);
               this.isLoading = false;
           })
   },
    handleSearch(query) {
        this.movies = [];
        this.isLoading = true;

        const url = `http://api.themoviedb.org/3/search/movie?api_key=4a455b69e26588bc7ba46001fdf4a5bb&query=${query}`;
        this.doQuery(url);
    }
  },
  created() {
      const url = 'https://api.themoviedb.org/3/discover/movie?language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&api_key=4a455b69e26588bc7ba46001fdf4a5bb'
      this.doQuery(url);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
