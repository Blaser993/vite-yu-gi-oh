<template>
  <Header></Header>
  <Main></Main>
  <Footer></Footer>
</template>

<script>

import Header from "/src/components/Header.vue";
import Main from "/src/components/Main.vue";
import Footer from "/src/components/Footer.vue";

export default{
  components: {
    Header,
    Main,
    Footer
  },


}

</script>
  


<style lang="scss" >
@use "./style/general.scss";

</style>
