<template lang="html">
  <div class="card" v-on:click="toggle()">
    <img class="character-icon" v-show="alive" :style="!alive ? opacityStyle : null" :src="require(`../assets/characters/${image}`)"/>
    <img class="character-icon" v-show="!alive" :style="!alive ? opacityStyle : null" :src="require(`../assets/characters/${dead_image}`)"/>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      index: Number,
      image: String,
      dead_image: String,
      alive:Boolean
    },
    data () {
      return {
        opacityStyle: {
          opacity: "80%"
        }
      }
    },
    methods: {
      toggle() {
        // Toggle alive status in parent, so the prop will be remembered between columns
        this.$emit("toggle", this.index);
      }
    }
  }
</script>
<style lang="css">
.card {
  display: inline-block;
  border: none;
  height: 100%;
  width: 100%;
  border-radius: 10px;
  background-color: transparent;
}

.character-icon {
  width: 80%;
  height: 70%;
  padding: 15px;
}
</style>
