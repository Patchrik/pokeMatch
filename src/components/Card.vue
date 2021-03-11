<template>
  <vue-flip width="7em" height="8em" active-click>
    <template v-slot:front>
      <v-card
        class="cardContainer"
        key="imageNum"
        @click="flipCard(Card.name, Card.number)"
      >
        <img
          :src="require('@/assets/pokeCards/Back-Card.png')"
          :alt="Card.name"
        />
      </v-card>
    </template>
    <template v-slot:back>
      <v-card
        class="cardContainer"
        key="imageNum"
        @click="flipCard(Card.name, Card.number)"
      >
        <img
          :src="require('@/assets/pokeCards/' + Card.image)"
          :alt="Card.name"
        />
      </v-card>
    </template>
  </vue-flip>
</template>

<script>
  import VueFlip from "vue-flip";
  export default {
    components: { "vue-flip": VueFlip },
    data() {
      return {
        facedown: true,
      };
    },
    props: {
      Card: Object,
    },
    methods: {
      flipCard(name, num) {
        console.log(name, num);
      },
    },
  };
</script>

<style scoped>
  .cardContainer {
    margin: 1em;
    max-width: 7em;
    height: auto;
  }

  img {
    max-width: 100%;
    max-height: 100%;
    display: block;
  }
</style>
