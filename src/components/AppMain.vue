<template>
      <Searchbar @searched="newSearch" />
      <FilmList :movies="filmList" />    
</template>
  
<script>
import Searchbar from './FilmSearchbar.vue';
import FilmList from './FilmList.vue';
import axios from 'axios';


  export default {
      name: 'AppMain',
      data(){
        return {
          filmList: [],
          moviesApiUrl: 'https://api.themoviedb.org/3/search/movie',
        }
      },
      components: {
      Searchbar,
      FilmList,
    },
    methods: {
        newSearch(searchInput){
        this.searchFilm(searchInput);
        this.searchSeries(searchInput);
        },
        searchFilm(searchInput){
            axios.get(this.moviesApiUrl, {
                    params: {
                        api_key: 'fe2a1f9ba227f29a481a922b0ab31857',
                        query : searchInput
                    }
                })
                .then( (response) => {
                    console.log(response.data.results);
                    this.filmList = response.data.results;
                   
                })
                .catch(function (error) {
                    console.log(error);
                })
        },
        searchSeries(searchInput){
            axios.get(this.seriesApiUrl, {
                    params: {
                        api_key: 'fe2a1f9ba227f29a481a922b0ab31857',
                        query : searchInput
                    }
                })
                .then( (response) => {
                    console.log(response.data.results);
                    this.seriesList = response.data.results;
                   
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
      
