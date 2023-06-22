<template>
    <div class="container">
        <div class="row justify-content-end">
            <div class="input-group mt-3 mb-4 w-75 ">
                <button @click="$emit('searched', searchedText)" type="button" class="input-group-text" id="basic-addon1">Search</button>
                <input type="text"  placeholder="Character name" aria-label="Character name" aria-describedby="basic-addon1"   v-model="searchedText">
            </div>
        </div>
    </div>
</template>
  
<script>

  export default {
      name: 'Searchbar',
      data(){
        return {
            searchedText:'',
  
        }
      },
      
  }
</script>
  
<style lang="scss" scoped>

input{
    width: 300px;
}


      
</style>