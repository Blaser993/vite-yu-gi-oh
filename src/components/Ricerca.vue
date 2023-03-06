<template>
    <input @keyup.enter="$emit('onSearch')" class="cerca" type="text" placeholder="Filtra una carta per nome..." v-model="store.ricerca">
</template>
  
<script>
  import store from "../store";

  export default{
    data(){
      return{
        store,
      }
    },


  }
  
</script>
    
  
  
  <style lang="scss" scoped>
  
  
  </style>