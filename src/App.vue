<template>
  <div id="app">
    <game-board />
  </div>
</template>

<script>
  import GameBoard from "./components/GameBoard.vue";

  export default {
    name: "App",
    components: { GameBoard },
    date() {
      return {
        backgroundColor: "#0D47A1",
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
    margin-top: 60px;
  }
  body {
    background-color: lightblue;
  }
</style>
