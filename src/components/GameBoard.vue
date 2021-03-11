<template>
  <v-container>
    <v-row>
      <div v-for="card in cardDeck" :key="card.id">
        <card :Card="card" />
      </div>
    </v-row>
  </v-container>
</template>

<script>
  import Card from "./Card.vue";
  export default {
    components: { Card },
    props: {
      cardDeck: Array,
    },
  };
</script>

<style></style>
