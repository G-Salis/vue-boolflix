<template>

  <main>

    <div class="container">

      <Card
      :movies="movies"
      :type="type"
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
        type: String
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