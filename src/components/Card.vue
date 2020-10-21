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
  border: 1px solid black;
}

.character-icon {
  width: 150px;
  height: 130px;
}
</style>
