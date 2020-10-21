<template lang="html">
  <b-card class="card">
    <img class="character-icon" :src="require(`../assets/characters/${image}`)"/>
  </b-card>
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
  border: none;
}

.character-icon {
  width: 6.9rem;
  height: 6rem;
}
</style>
