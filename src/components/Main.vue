<template>
    <h1>MAin</h1>

    <ul v-for="monster in monsters" :key="monster.id">

        <figure v-for="image in monster.card_images" :key="image.id">
            <img :src="image.url_image" alt="pic">
        </figure>
        
        
        <h2>{{monster.name}}</h2>
    </ul>
</template>
  
  <script>
  import axios from "axios";

  export default{
    data(){
    return{
      monsters:[""],
      card_images:[""]
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
  
  
  </style>