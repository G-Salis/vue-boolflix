<template>

<div class="card">
    <ul v-for="movie in movies" 
    :key="movie.id">
      <li v-if="type === 'movie'">{{movie.title}}</li>
      <li v-else>{{movie.name}}</li>
      <li>

        <div class="flip-card">
          <div class="flip-card-inner">
            <div class="flip-card-front">
              <img v-if="movie.poster_path != null"
              :src="`http://image.tmdb.org/t/p/w300/${movie.poster_path}`" alt="">
              <div v-else  class="img-default">NO IMAGE</div>
            </div>
            <div class="flip-card-back">
              
              <p>TRAMA:{{movie.overview}}</p>
            
            </div>
          </div>
        </div>
          
      </li>
        
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
  background-color: #2E3A46;
  margin: 20px;
  }
.flags{
  width: 30px;
}
.img-default{
  background-color: blue;
  width: 300px;
  height: 450px;
  text-align: center;
}
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 450px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  color: black;
}

.flip-card-back {
  background-color: darkred;
  color: white;
  transform: rotateY(180deg);
  overflow: auto;
}
</style>



