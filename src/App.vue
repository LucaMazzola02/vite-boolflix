<script>
import AppMain from './components/AppMain.vue';


export default {
    name: 'App',
    data(){
      return {

      }
    },
    components: {
      AppMain,     
    }
}
</script>

<template>
  <AppMain />
</template>

<style lang="scss">
    @import 'bootstrap/scss/bootstrap';
    @import './styles/general.scss';
</style>
