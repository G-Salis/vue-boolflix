<template>
  <div id="app">

    <Nav @search="searchToMain"/>
    <Main :movies="movies"/>
  
 
  </div>
</template>

<script>
import Nav from "./components/Nav.vue"
import Main from "./components/Main.vue"
import axios from "axios"

export default {
  name: 'App',
  components: {

    Nav,
    Main,
  
  },

    data(){
    return{
      navSearch:'',
      movies: [],
    }
  },
    methods:{
    searchToMain(search){
      this.navSearch = search;
      console.log(this.navSearch);
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c50fb50991ae68804531ae453cb59c3e&query=${this.navSearch}`)
      .then(r =>{
          this.movies = r.data.results;
          console.log('dopo', this.navSearch);
          console.log(this.movies);
        })
    }
  }

}
</script>

<style lang="scss">
@import "./assets/style/generals.scss";
@import "./assets/style/utilities.scss";
</style>