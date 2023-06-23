<template>
      <article v-for="movie in movies" class="card mb-5 col-6 p-0">
        <div class="card-body text-center">
            <h2 class="card-title fw-bold">
                {{ movie.title }}   
            </h2>
            <em><h4>{{ movie.original_title }}</h4></em>
            <p class="movies-vote">
                VOTO : {{ movie.vote_average }} 
            </p>   

            <p v-if="!availableLanguages.includes(movie.orginal_language)" class="movies-language">
              {{ movie.orginal_language }}
            </p>
            <img v-else :src="`/flags/$(movie.orginal_language).png`"/>
        </div>
    </article>
</template>

<script>
export default {
    name: 'FilmList',
    props:{
      movies : Array
    },
    data : {
      return : {
        availableLanguages : ["it","en","es","fr","ja","dt"]
      }
    },
}
</script>



<style lang="scss" scoped>

article img{width: 30px;}

</style>
