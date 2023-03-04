<template>
    <h1>MAin</h1>

    <div class="container">

      <!-- <ul class="cards" >
        <li class="monster card" v-for="monster in monsters" :key="monster.id">
          
          <img :src="monster.card_images[0].image_url" alt="pic">
                
          <h2>{{monster.name}}</h2>
        </li>
      </ul> -->

      <Monster class="monster card" v-for="element in monsters" :key="monsters.id" :monster="element"></Monster>
    </div>
    
</template>
  
  <script>
  import axios from "axios";
  import Monster from "./Monster.vue";

  export default{
    components:{
      Monster,
    },
    data(){
      return{
        monsters:[""],
        
      }   
  },
    methods: {
        fetchMonsters(){
            console.log("fetching monsters")
            axios
                .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0")
                .then((res) => {
                    
                    this.monsters = res.data.data
                    console.log(this.monsters)
                    console.log("prova:", this.monsters[0].card_images[0].image_url, this.monsters[0].name)
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
      grid-template-columns: repeat(3,1fr);
    }
  </style>