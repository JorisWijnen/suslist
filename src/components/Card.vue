<template lang="html">
  <div class="card">
    <img class="character-icon" :src="require(`../assets/characters/${image}`)"/>
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: {
      image: String
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
