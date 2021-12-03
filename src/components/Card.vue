<template>

<div class="card">
    <ul v-for="movie in movies" 
    :key="movie.id">
      <li v-if="type === 'movie'">{{movie.title}}</li>
      <li v-else>{{movie.name}}</li>
      <li><img :src="`http://image.tmdb.org/t/p/w300/${movie.poster_path}`" alt=""></li>
      <li v-if="type === 'movie'">Titolo Originale: {{movie.original_title}}</li>
      <li v-else>Titolo Originale: {{movie.original_name}}</li>
      <li><img class="flags"
        v-if="flags.includes(movie.original_language)"
       :src="require(`../assets/img/${movie.original_language}.png`)" :alt="movie.title">
       <p v-else>Lingua: {{movie.original_language}}</p>
       </li>
      <li>{{Math.round(movie.vote_average/2)}}</li>
      <li>
        <i 
        v-for="(star, index) in 5"
        :key="index"
        class="fa-star"
        :class="index < Math.round(movie.vote_average/2) ? 'fas' : 'far' "
        ></i>
      </li>
    </ul>
  </div>
    
  
</template>

<script>
export default {

  name: "Card",
  props:{
    movies: Array,
    type: String
  },
  data(){
    return {
      flags: ['it', 'en']
    }
  }

}
</script>

<style>
@import "~@fortawesome/fontawesome-free/css/all.min.css";
.card{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
ul{
  list-style: none;
  text-align: center;
  background-color: darkred;
  margin: 20px;
  }
.flags{
  width: 30px;
}
</style>