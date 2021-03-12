<template>
  <v-container class="game-board">
    <a href="https://fontmeme.com/pokemon-font/"
      ><img
        src="https://fontmeme.com/permalink/210312/5014fc4c0ac365b0e9c7d7a317c492fe.png"
        alt="pokemon-font"
        border="0"
    /></a>
    <v-snackbar :value="snackBool" :color="snackColor" top left>
      {{ snackText }}
    </v-snackbar>
    <h2>{{ gameStatus }}</h2>
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
        snackBool: false,
        snackText: "",
        snackColor: "grey-darken-3",
        guesses: 0,
      };
    },
    methods: {
      handleMatching() {
        if (this.guess1.number === this.guess2.number) {
          this.matched.push(this.guess2);
          this.guesses++;
          this.handleSnack({
            msg: "You Found A Match!",
            bool: true,
            color: "light-green lighten-2",
          });

          setTimeout(() => {
            this.guess1 = null;
            this.guess2 = null;
          }, 5);
        } else {
          this.guesses++;
          this.handleSnack({
            msg: "No Match!",
            bool: true,
            color: "red lighten-1",
          });

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
        this.snackBool = item.bool;
        this.snackText = item.msg;
        this.snackColor = item.color;
        setTimeout(() => {
          this.snackBool = !this.snackBool;
        }, 1500);
      },
    },
    computed: {
      gameStatus() {
        const score = this.matched.length;
        if (score >= 12) {
          return `Looks like it took you ${this.guesses} Guesses to Match Em' All!`;
        } else if (score > 6 && score < 12) {
          return `Looks like you're getting close?  You've Made ${this.guesses} Guesses`;
        } else {
          return `Gotta Match 'Em All! You've Made ${this.guesses} Guesses`;
        }
      },
    },
  };
</script>

<style></style>
