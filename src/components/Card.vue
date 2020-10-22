<template lang="html">
  <div class="card" v-on:click="toggle()">
    <img class="character-icon" :style="!alive ? opacityStyle : null" :src="require(`../assets/characters/${image}`)"/>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      index: Number,
      image: String,
      alive:Boolean
    },
    data () {
      return {
        opacityStyle: {
          opacity: "20%"
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
