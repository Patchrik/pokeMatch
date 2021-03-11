<template>
  <div id="app">
    <game-board :cardDeck="deck" />
  </div>
</template>

<script>
  import GameBoard from "./components/GameBoard.vue";
  import getPokemonCards from "@/data";
  import shuffle from "lodash.shuffle";
  export default {
    name: "App",
    components: { GameBoard },
    data() {
      return {
        deck: shuffle(getPokemonCards()),
      };
    },
  };
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
