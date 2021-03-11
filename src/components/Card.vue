<template>
  <vue-flip
    width="7em"
    height="8em"
    v-model="Card.unmatched"
    @click.native="clickCard(Card)"
  >
    <template v-slot:front>
      <v-card class="cardContainer" key="imageNum">
        <img
          :src="require('@/assets/pokeCards/' + Card.image)"
          :alt="Card.name"
        />
      </v-card>
    </template>
    <template v-slot:back>
      <v-card class="cardContainer" key="imageNum">
        <img
          :src="require('@/assets/pokeCards/Back-Card.png')"
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
      return {};
    },
    props: ["Card", "Guess1", "Guess2"],
    methods: {
      clickCard(Card) {
        if (Card.unmatched === false) {
          console.log("You've already clicked that card");
          this.$emit("snack-msg", {
            msg: "You've already clicked that card",
            bool: true,
          });
          return;
        } else if (this.Guess1 != null && this.Guess2 != null) {
          console.log("You've made 2 guesses!");
          this.$emit("snack-msg", {
            msg: "You've already made 2 guesses!",
            bool: true,
          });
          return;
        }
        this.$emit("card-clicked", Card);
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
