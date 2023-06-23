<template>
    <div class="container">
      <div class="row text-center">
        <h1 class="mb-3">Serie TV</h1>
        <article v-for="serie in series" class="card mb-5 col-3 p-0">
          <div class="card-body text-center">
              <h2 class="card-title fw-bold">
                  {{ serie.name }}   
              </h2>
              <em><h4>{{ serie.original_name }}</h4></em>
               
              <img v-if="isLanguageAvailable(serie.original_language)" 
              :src="getImagePath(serie.original_language)" alt="language-image"/> 
  
              <span v-else>
                {{ serie.original_language }}
              </span>
              
              <p class="movies-vote">
                  VOTO : {{ serie.vote_average }} 
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
        series : Array
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
  
  
  