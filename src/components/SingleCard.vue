<template>
    <article>
        <div class="card-body text-center">
            <div class="card-image">
            <img :src="`https://image.tmdb.org/t/p/w342${movie.poster_path}`" alt="NO-IMAGE">
            </div>
            <div class="description">            
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
                    <i class="fa-solid fa-star font-yellow" v-for="n in 5 - getVote"></i>
                    <i class="fa-solid fa-star font-grey" v-for="n in getVote"></i>
                </p>

            </div>
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
      },
    },
    computed : {
        getVote(){
        return Math.ceil(this.movie.vote_average/2);
      }
    }
      
  }
</script>
  
<style lang="scss" scoped>

   article img{width: 30px;}
   .card-image{
    display: block;
    width: 100%;
    height: 100%;
    
    
    & img{
        width: 100%;
        height: 100%;
    }
   }
   .description{
    display: none;
   }
   .card-body:hover .card-image{
    display: none;
    
   }
   .card-body:hover .description{
    display: block;
   }

   .font-grey{
    color: grey;
   }
   .font-yellow{
    color: goldenrod;
   }
</style>