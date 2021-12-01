<template>
  <header>
  
   <div class="container">

     <div>
        <h1>Boolflix</h1>
     </div>
     <div class="inp">
       <input  v-model="search" @keyup.13="sendToMedia" type="text">
     </div>
    
        
   </div>
    
  </header>
</template>

<script>
  
  export default {
  name: 'Nav',

    data(){
          return{
              search: '',
          }
    },

    methods:{
        sendToMedia(){
            this.$emit('search', this.search);
            this.search = '';
        }
    },

    mounted(){
        this.sendToMedia()
    },
  }
</script>



<style lang="scss" >
  header{
    background-color: #2E3A46;
    height: 70px;
    .container{
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      flex-wrap: wrap;
      width: 60%;
      margin: 0 auto;
      min-height: 150px;
    }
    h1{
      padding: 15% 0px;
    }
    .inp{
        padding-top: 10px;
        input{
          color: black;
        }
    }
  }
</style>