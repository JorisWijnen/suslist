<template>
  <div class="dashboard">
    <div>
      <Card v-for="(image, index) in images" :key="index" :image='image'/>
    </div>
  </div>
</template>


<script>
import Card from './Card.vue'

export default {
    name: "DashBoard",
    components: {
      Card
    },
    data() {
      return {
        images: [
          "blackcrewpng.png",
          "bluecrewpng.png",
          "browncrewpng.png",
          "cyancrewpng.png",
          "greencrewpng.png",
          "limecrewpng.png",
          "orangecrewpng.png",
          "pinkcrewpng.png",
          "purplecrewpng.png",
          "redcrewpng.png",
          "whitecrewpng.png",
          "yellowcrewpng.png"
        ]
      }
    }
  }
</script>

<style lang="css">
</style>
