<template>

<div>
    <ul v-for="movie in movies" 
    :key="movie.id">
      <li>{{movie.title}}</li>
      <li>{{movie.original_title}}</li>
      <li><img
        v-if="flags.includes(movie.original_language)"
       :src="require(`../assets/img/${movie.original_language}.png`)" :alt="movie.title">
       <p v-else>Lingua: {{movie.original_language}}</p>
       </li>
      <li>{{movie.vote_average}}</li>
    </ul>
  </div>
    
  
</template>

<script>
export default {

  name: "Card",
  props:{
    movies: Array
  },
  data(){
    return {
      flags: ['it', 'en']
    }
  }

}
</script>

<style>
ul{
  list-style: none;
  text-align: center;
  background-color: darkred;
  margin: 20px;
  }
img{
  width: 30px;
}
</style>