<template>
  <div class="columns is-multiline" v-if="gifs">
    <div class="column is-one-third" v-for="gif in gifs" :key="gif.id">
      <gif-box :gif="gif"></gif-box>
    </div>
  </div>
</template>

<script>
import GifBox from "./GifBox";

export default {
  name: "gif-grid",
  components: {
    GifBox
  },
  props: {
    gifs: Array
  }
};
</script>

<style scoped>
</style>