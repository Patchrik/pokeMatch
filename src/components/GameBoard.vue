<template>
  <v-container class="game-board">
    <h1>{{ gameStatus }}</h1>
    <v-row>
      <div v-for="card in cardDeck" :key="card.id">
        <card
          :Card="card"
          :Guess1="guess1"
          :Guess2="guess2"
          @card-clicked="handleFlip"
          @snack-msg="handleSnack"
        />
      </div>
    </v-row>
    <v-snackbar :value="snack" bottom color="red" right rounded="pill">
      {{ snackText }}
    </v-snackbar>
  </v-container>
</template>

<script>
  import Card from "./Card.vue";
  import getPokemonCards from "@/data.js";
  import shuffle from "lodash.shuffle";
  export default {
    components: { Card },
    data() {
      return {
        cardDeck: shuffle(getPokemonCards()),
        guess1: null,
        guess2: null,
        matched: [],
        snack: false,
        snackText: "",
      };
    },
    methods: {
      handleMatching() {
        if (this.guess1.number === this.guess2.number) {
          console.log("You matched");
          this.matched.push(this.guess2);
          console.log(this.matched.length);

          setTimeout(() => {
            this.guess1 = null;
            this.guess2 = null;
          }, 5);
        } else {
          console.log("No match");
          setTimeout(() => {
            this.guess1.unmatched = true;
            this.guess2.unmatched = true;
          }, 1000);
          setTimeout(() => {
            this.guess1 = null;
            this.guess2 = null;
          }, 1001);
        }
      },
      handleFlip(item) {
        if (!this.guess1 && !this.guess2) {
          this.guess1 = item;
          item.unmatched = !item.unmatched;
          console.log(this.guess1);
        } else if (this.guess1 && !this.guess2 && item.id !== this.guess1.id) {
          this.guess2 = item;
          item.unmatched = !item.unmatched;
          console.log(this.guess2);
        }

        if (this.guess1 && this.guess2) {
          this.handleMatching();
        }
      },
      handleSnack(item) {
        this.snack = item.bool;
        this.snackText = item.msg;
        setTimeout(() => {
          this.snack = !this.snack;
        }, 1000);
      },
    },
    computed: {
      gameStatus() {
        const score = this.matched.length;
        if (score >= 12) {
          return "Are you winning, son? Looks like you're winning";
        } else if (score > 6 && score < 12) {
          return "Looks like you're getting close?";
        } else {
          return "You just blow in from stupid town?";
        }
      },
    },
  };
</script>

<style>
  .game-board {
    background-image: url("/src/assets/bg-gym.jpg") repeat 0 0;
  }
</style>
