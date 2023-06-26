<template>
  <div class="container">
    <div class="row text-center">
      <SingleCard v-for="movie in movies" class="card mb-5 col-3 p-0" :movie="movie" />    
    </div>
  </div>
      
</template>

<script>
import SingleCard from './SingleCard.vue';

export default {
    name: 'FilmList',
    components : {
      SingleCard,
    },
    props:{
      movies : Array
    },
}    
</script>



<style lang="scss" scoped>
</style>


