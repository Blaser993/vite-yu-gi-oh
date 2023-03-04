<template>


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

  export default{
    components:{
      Monster,
    },
    data(){
      return{
        monsters:[""],
        store
      }   
  },
    methods: {
        fetchMonsters(){
            console.log("fetching monsters")
            axios
              .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
              .then((res) => {
                  
                  this.store.monsters = res.data.data
                  console.log(this.store.monsters)
              })
        }
    },
    created(){
        this.fetchMonsters()
    },
  }
  
  </script>
    
  
  
  <style lang="scss" scoped>
  
    .monster{
      border: red solid 2px;
      text-align: center;
      img{
        max-height: 600px;
      }
    }

    .cards{
      display: grid;
      gap: 3rem;
      grid-template-columns: repeat(4,1fr);
    }
  </style>