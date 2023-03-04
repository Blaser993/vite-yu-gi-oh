<template>
        <li class="monster card">
          
          <img :src="monster.card_images[0].image_url" alt="pic">
                
          <h2>{{monster.name}}</h2>
        </li>
</template>
  
<script>
  export default{
    props:{
      monster: {
        type: Object,
        required: true
      }
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
  
  </style>