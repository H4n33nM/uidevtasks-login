<template>
  <!--start here-->
  <div class="hello">
    hello!
  </div>

  <div class="image">
    <img :src="flowersImage" alt="Flowers" />
  </div>
</template>


<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      flowersImage: require('@/assets/flowers.png')
    }
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.image {
  position: absolute;
  width: 720px;
  height: 1024px;
  left: 0px;
  top: 0px;
}
</style>
