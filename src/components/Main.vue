<template>

  <main>

    <div class="container">

      <Card
      :movies="movies"
      />
      
    </div>

  </main>

</template>

<script>
import Card from "./Card.vue";

  export default {
  name: 'Main',
    components:{
    Card,
  },
   props:{
        movies: Array,
    },
  }

</script>

<style lang="scss">
  main{
    background-color: #1E2D3B;
    min-height: calc(100vh - 70px);
    padding: 40px 0px;
  }
</style>