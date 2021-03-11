<template>
  <div id="app">
    <div v-for="card in deck" :key="card.id">
      <img :alt="card.name" :src="card.img" />
      <card :imageName="card.name" :imageSRC="card.img" />
    </div>
  </div>
</template>

<script>
  import Card from "./components/Card.vue";
  // import shuffle from "lodash.shuffle";

  export default {
    name: "App",
    components: { Card },
    data() {
      return {
        deck: [
          {
            id: 1,
            name: "Alakazam",
            number: 1,
            img: "Alakazam-Card.jpg",
          },
          {
            id: 2,
            name: "Blastoise",
            number: 2,
            img: "Blastoise-Card.jpg",
          },
          {
            id: 3,
            name: "Chansey",
            number: 3,
            img: "Chansey-Card.jpg",
          },
          {
            id: 4,
            name: "Charizard",
            number: 4,
            img: "Charizard-Card.jpg",
          },
          {
            id: 5,
            name: "Clefairy",
            number: 5,
            img: "Clefairy-Card.jpg",
          },
          {
            id: 6,
            name: "Gyarados",
            number: 6,
            img: "Gyarados-Card.jpg",
          },
          {
            id: 7,
            name: "Hitmonchan",
            number: 7,
            img: "Hitmonchan-Card.jpg",
          },
          {
            id: 8,
            name: "Machamp",
            number: 8,
            img: "Machamp-Card.jpg",
          },
          {
            id: 9,
            name: "Mewtwo",
            number: 9,
            img: "Mewtwo-Card.jpg",
          },
          {
            id: 10,
            name: "Ninetales",
            number: 10,
            img: "Ninetales-Card.jpg",
          },
          {
            id: 11,
            name: "Raichu",
            number: 11,
            img: "Raichu-Card.jpg",
          },
          {
            id: 12,
            name: "Venusaur",
            number: 12,
            img: "Venusaur-Card.jpg",
          },
          {
            id: 13,
            name: "Alakazam",
            number: 1,
            img: "Alakazam-Card.jpg",
          },
          {
            id: 14,
            name: "Blastoise",
            number: 2,
            img: "Blastoise-Card.jpg",
          },
          {
            id: 15,
            name: "Chansey",
            number: 3,
            img: "Chansey-Card.jpg",
          },
          {
            id: 16,
            name: "Charizard",
            number: 4,
            img: "Charizard-Card.jpg",
          },
          {
            id: 17,
            name: "Clefairy",
            number: 5,
            img: "Clefairy-Card.jpg",
          },
          {
            id: 18,
            name: "Gyarados",
            number: 6,
            img: "Gyarados-Card.jpg",
          },
          {
            id: 19,
            name: "Hitmonchan",
            number: 7,
            img: "Hitmonchan-Card.jpg",
          },
          {
            id: 20,
            name: "Machamp",
            number: 8,
            img: "Machamp-Card.jpg",
          },
          {
            id: 21,
            name: "Mewtwo",
            number: 9,
            img: "Mewtwo-Card.jpg",
          },
          {
            id: 22,
            name: "Ninetales",
            number: 10,
            img: "Ninetales-Card.jpg",
          },
          {
            id: 23,
            name: "Raichu",
            number: 11,
            img: "Raichu-Card.jpg",
          },
          {
            id: 24,
            name: "Venusaur",
            number: 12,
            img: "Venusaur-Card.jpg",
          },
        ],
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
