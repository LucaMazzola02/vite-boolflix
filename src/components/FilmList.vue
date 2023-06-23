<template>
  <div class="container">
    <div class="row text-center">
      <h1 class="mb-3">Film</h1>
      <article v-for="movie in movies" class="card mb-5 col-3 p-0">
        <div class="card-body text-center">
            <h2 class="card-title fw-bold">
                {{ movie.title }}   
            </h2>
            <em><h4>{{ movie.original_title }}</h4></em>
             
            <img v-if="isLanguageAvailable(movie.original_language)" 
            :src="getImagePath(movie.original_language)" alt="language-image"/> 

            <span v-else>
              {{ movie.original_language }}
            </span>
            
            <p class="movies-vote">
                VOTO : {{ movie.vote_average }} 
            </p> 
        </div>
      </article>
    </div>
  </div>
      
</template>

<script>
export default {
    name: 'FilmList',
    props:{
      movies : Array
    },
    data (){
      return {
        availableLanguages : ['it.png','en.png','es.png','fr.png','ja.png','dt.png']
      }
    },

    methods :{
      isLanguageAvailable(language){
        if(this.availableLanguages.includes(language + '.png')){
          return true
        }

        return false;
      },
      getImagePath(img){
        return new URL(`../assets/flags/${img}.png`, import.meta.url).href;
      }

    },
}    
</script>



<style lang="scss" scoped>

h1{
    font-size: 55px;
    font-weight: bolder;
    color: coral;
  }
  

article img{width: 30px;}

</style>


