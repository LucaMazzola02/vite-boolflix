<template>
  <Searchbar @searched="searchFilm" />
</template>

<script>
import Searchbar from './FilmSearchbar.vue';
import axios from 'axios'

export default {
    name: 'AppHeader',
    data(){
      return {
        filmList: [],
        apiUrl: 'https://api.themoviedb.org/3/search/movie?api_key=fe2a1f9ba227f29a481a922b0ab31857&query=',

      }
    },
    components: {
      Searchbar,
    },
    methods: {
        searchFilm(needle = ''){
            axios.get(this.apiUrl, {
                    params: {
                        name: needle
                    }
                })
                .then( (response) => {

                    console.log(response);
                    

                })
                .catch(function (error) {
                    console.log(error);
                })
        }
    },


    created(){
        this.searchFilm();
    }
    
}
</script>

<style lang="scss">
    
</style>