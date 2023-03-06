<template>
        <li class="monster card" >
          
          <img  :src="monster.card_images[0].image_url" alt="pic">
                
          <h2 class="nome">{{monster.name}}</h2>

          <span class="archetipo"> {{monster.archetype}}</span>
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
      border-radius: 12px;
      padding: .75rem;
      background-color:rgb(249, 249, 249);
      color: black;
      text-align: center;
      display: flex;
      flex-direction: column;
      
      
        img{
          max-height: 600px;
          
        }

        .nome{
          font-size: 1.25rem;
          margin-top: .75rem;
        }

        .archetipo{
          margin-top: auto;
        }
    }
  
  </style>