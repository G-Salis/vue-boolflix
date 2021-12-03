<template>
  <div id="app">

    <Nav @search="searchMedia"/>
    <Main :type="types.movie" :movies="contents.movie"/>
    <Main :type="types.tv" :movies="contents.tv"/>
  
 
  </div>
</template>

<script>

// import Nav from "./components/Nav.vue"
// import Main from "./components/Main.vue"
// import axios from "axios"
// export default {
//   name: 'App',
//   components: {
//     Nav,
//     Main,
  
//   },
//     data(){
//     return{
//       navSearch:'',
//       film: [],
//     }
//   },
//     methods:{
//     searchMedia(search){
//       this.navSearch = search;
//       console.log(this.navSearch);
//       axios.get(`https://api.themoviedb.org/3/search/movie?api_key=c50fb50991ae68804531ae453cb59c3e&query=${this.navSearch}`)
//       .then(r =>{
//           this.film = r.data.results;
//           console.log('src', this.navSearch);
//           console.log(this.film);
//         })
//     }
//   }
// }





// --------------------------------------------------------
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
      contents:{
        movie:[],
        tv:[]
      },

     types:{
       movie: 'movie',
        tv: 'tv'
    },
    
      text:'',
      type:'',
      apiUrl: 'https://api.themoviedb.org/3/search/',
      apiParams :{
        api_key: 'c50fb50991ae68804531ae453cb59c3e',
        language: 'it-IT',
        query: this.searchMedia
      }
    }
  },
    methods:{
    getApi(type){
      axios.get(this.apiUrl+type, {params: this.apiParams})
      .then(r =>{
          this.contents[type] = r.data.results;
        })
        .catch(err => {
          console.log('error',err);
        })
    },
    searchMedia(text){
      this.apiParams.query = text;
       console.log('src',text);
      this.getApi('movie');
      this.getApi('tv');
    }
  },
  mounted(){
    this.getApi('movie');
    this.getApi('tv');
  }

}
</script>

<style lang="scss">
@import "./assets/style/generals.scss";
@import "./assets/style/utilities.scss";
</style>