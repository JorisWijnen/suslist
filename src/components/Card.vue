<template lang="html">
  <div class="card" v-on:click="toggle()">
    <img class="character-icon" :style="!alive ? opacityStyle : null" :src="require(`../assets/characters/${image}`)"/>
    <v-overlay></v-overlay>
    <!-- <button v-on:click="toggle()">Toggle</button> -->
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      image: String
    },
    data () {
      return {
        alive:true,
        opacityStyle: {
          opacity: "20%"
        }
      }
    },
    methods: {
      toggle: function() {
        this.alive = !this.alive
      }
    }
  }
</script>
<style lang="css">
.card {
  display: inline-block;
  border: 1px solid grey;
  height: 100%;
  width: 100%;
  border-radius: 10px;
}

.character-icon {
  width: 80%;
  height: 70%;
  padding: 15px;
}
</style>
