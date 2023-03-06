<template>
    <input @keyup.enter="onEnter" class="cerca" type="text" placeholder="Filtra una carta per nome..." v-model="store.ricerca">
</template>
  
<script>
  import store from "../store"

  export default{
    data(){
      return{
        store,
      }
    },
    methods:{
      onEnter(){    
          console.log("ho cercato", this.store.ricerca)
          this.$emit("onSearch")
        }
    }

  }
  
</script>
    
  
  
  <style lang="scss" scoped>
  
  
  </style>