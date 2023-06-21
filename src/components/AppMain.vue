<template>
    <FilmList />
    <SingleFilmCard />
    
</template>
  
<script>
import FilmList from './FilmList.vue';
import SingleFilmCard from './SingleFilmCard.vue';

  export default {
      name: 'AppMain',
      data(){
        return {
  
        }
      },
      components: {
      FilmList,
      SingleFilmCard,
    },
      
  }
</script>
  
<style lang="scss">
      
</style>