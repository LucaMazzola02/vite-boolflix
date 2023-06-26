<template>
    <article>
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
            
            <p class="movies-vote mt-3">
                VOTO : {{ movie.vote_average }} <i class="fa-solid fa-star"></i>
            </p> 
        </div>
      </article>   
</template>
  
<script>

  export default {
      name: 'singleCard',
      data(){
        return {
        availableLanguages : ['it.png','en.png','es.png','fr.png','ja.png','dt.png']
        }
      },
      props : {
        movie : Object,
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

   article img{width: 30px;}
 
</style>