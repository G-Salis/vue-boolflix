<template>
  <main>

    <div class="container">

      <div v-for="(movie, index) in movies" :key="index">
        <ul>
            <li>{{movie.title}}</li>
            <li>{{movie.original_title}}</li>
            <li>{{movie.original_language}}</li>
            <li>{{movie.vote_average}}</li>
        </ul>
      </div>
        
      
    </div>

  </main>

</template>

<script>

  export default {
  name: 'Main',
   props:{
        movies: Array,
    },
  }

</script>

<style lang="scss">
  main{
    background-color: #1E2D3B;
    height: calc(100vh - 70px);
    padding: 40px 0px;
    ul{
      list-style: none;
      text-align: center;
      background-color: darkred;
      margin: 20px;
    }
  }
</style>