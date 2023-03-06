<template>

  <div class="filtri">
    <!-- <input @keyup.enter="onEnter" class="cerca" type="text" placeholder="Filtra una carta per nome..." v-model="store.ricerca"> -->
    <Ricerca @onSearch="onSearchFn"></Ricerca>
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
          const ricerca = this.store.ricerca
            console.log("fetching monsters", ricerca)

            axios
              // .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?offset=0&num=20&fname="+ricerca)
              .get("https://db.ygoprodeck.com/api/v7/cardinfo.php",{
                params:{
                  num: 20,
                  offset: 0,
                  fname: ricerca
                }
              })

              .then((res) => {
                  
                  this.store.monsters = res.data.data
                  console.log(this.store.monsters)
              })
        },
        onSearchFn(){
          console.log("on search event")
          this.fetchMonsters()
        }

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