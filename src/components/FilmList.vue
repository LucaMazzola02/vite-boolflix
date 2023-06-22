<script>
export default {
    name: 'FilmList',
    props:{
      movies : Array
    }
}
</script>

<template>
  <article v-for="movie in movies">
      <h2>{{ movie.original_title }}</h2>
      <h4>{{ movie.title }}</h4>
  </article>
  
</template>

<style lang="scss">

</style>
