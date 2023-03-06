<template>
    <input @keyup.enter="$emit(onClick)" class="cerca" type="text" placeholder="Filtra una carta per nome..." v-model="store.ricerca">
</template>
  
  <script>
  export default{
    data(){
      return{
        store,
      },
    },
    methods: {
      onClick(){
          console.log("ho cercato", this.store.ricerca, "poi" ,this.ricerca)
        }
    }
  }
  
  </script>
    
  
  
  <style lang="scss" scoped>
  
  
  </style>