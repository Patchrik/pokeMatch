<template>
  <img :src="require('@/assets/pokeCards/' + imageSRC)" :alt="imageName" />
</template>

<script>
  export default {
    props: {
      imageSRC: String,
      imageName: String,
    },
  };
</script>

<style></style>
