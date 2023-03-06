<template>

  <div class="filtri">
    <!-- <input @keyup.enter="onEnter" class="cerca" type="text" placeholder="Filtra una carta per nome..." v-model="store.ricerca"> -->
    <Ricerca></Ricerca>
    {{store.ricerca}}
  </div>

    <div class="container">
      <ul class="cards">
        <Monster class="monster card" v-for="element in store.monsters" :key="monsters.id" :monster="element"></Monster>
      </ul>
    </div>
    
</template>
  
  <script>
  import axios from "axios";
  import store from "../store";
  import Monster from "./Monster.vue";
  import Ricerca from "./Ricerca.vue";

  export default{
    components:{
      Monster,
      Ricerca,
    },
    data(){
      return{
        
        monsters:[""],
        store,
        
      }   
  },
    methods: {
        fetchMonsters(){
            console.log("fetching monsters")
            axios
              .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=40&offset=0")
              .then((res) => {
                  
                  this.store.monsters = res.data.data
                  console.log(this.store.monsters)
              })
        },

    },
    created(){
        this.fetchMonsters()
    },
  }
  
  </script>
    
  
  
  <style lang="scss" scoped>
  


    .cards{
      padding: 3rem;
      display: grid;
      gap: .75rem;
      grid-template-columns: repeat(4,1fr);
    }

    .filtri{
      position: sticky ;
      top: 0;
      padding: 1rem;
      background-color: rgba($color: #fafafa, $alpha: .1);
    }

    .cerca{
      line-height: 36px;
      padding: 0.5rem 1rem;
      font-size: 22px;
      margin: 0 3rem;
      margin-top: .5rem;
      margin-bottom: 0.5rem;
      border-radius: 12px;
    }
  </style>