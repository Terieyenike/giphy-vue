<template>
  <section class="section container">
    <!-- SEARCH ========================================== -->
    <h2 class="title">Search</h2>

    <input type="text" class="input" name="query" v-model="query" @keyup.enter="searchGifs" />
    <gif-grid :gifs="searchedGifs"></gif-grid>

    <!-- TRENDING ======================================= -->
    <h2 class="title">Trending</h2>

    <gif-grid :gifs="trendingGifs"></gif-grid>
  </section>
</template>

<script>
import GifGrid from "./components/GifGrid";
export default {
  components: {
    GifGrid
  },
  data() {
    return {
      apiUrl: "http://api.giphy.com/v1/gifs",
      apiKey: process.env.VUE_APP_API_KEY,
      trendingGifs: null,
      searchedGifs: null,
      query: ""
    };
  },
  methods: {
    fetchGifs() {
      const url = `${this.apiUrl}/trending?api_key=${this.apiKey}`;

      fetch(url)
        .then(response => response.json())
        .then(data => (this.trendingGifs = data.data));
    },
    searchGifs() {
      const url = `${this.apiUrl}/search?api_key=${this.apiKey}&q=${this.query}&limit=8`;

      fetch(url)
        .then(response => response.json())
        .then(data => (this.searchedGifs = data.data));
      this.query = "";
    }
  },
  created() {
    this.fetchGifs();
  }
};
</script>

<style>
input[type="text"] {
  margin-bottom: 2em;
}

.gif-box {
  position: relative;
  background: #333;
}
.gif-user {
  display: flex;
  align-items: center;
  position: absolute;
  left: 15px;
  bottom: 15px;
}
.gif-user img {
  margin-right: 8px;
}
</style>
