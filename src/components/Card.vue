<template>
  <v-card class="cardContainer">
    <img :src="require('@/assets/pokeCards/' + imageSRC)" :alt="imageName" />
  </v-card>
</template>

<script>
  export default {
    props: {
      imageSRC: String,
      imageName: String,
    },
  };
</script>

<style>
  cardContainer {
    margin: 1em;
    padding: 1em;
    max-width: 4em;
    height: auto;
  }
</style>
