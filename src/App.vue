<template>
  <div in="App">
    <Header @sendRequest="searchMovie" />

    <Main :arrayMovies="movieList" :arraySeries="tvList" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      api: "https://api.themoviedb.org/3/search",
      movieList: [],
      tvList: [],
      apiKey: "e12447a41ebd0cc2c67454fb0200dd04",
    };
  },
  computed: {},
  created() {},
  methods: {
    // getMovie() {
    //   axios
    //     .get(this.api + "/movie", {
    //       params: {
    //         api_key: this.apiKey,
    //         query: this.search,
    //         // CORREZIONE
    //         language: "it-IT",
    //       },
    //     })
    //     .then((res) => {
    //       this.movieList = res.data.results;
    //       console.log(this.movieList);
    //     })
    //     .catch((error) => {
    //       console.log(error, "Error");
    //     });
    //   axios
    //     .get(this.api + "/tv", {
    //       params: {
    //         api_key: this.apiKey,
    //         query: this.search,
    //         language: "it-IT",
    //       },
    //     })
    //     .then((res) => {
    //       this.tvList = res.data.results;
    //       console.log(this.tvList);
    //     })
    //     .catch((error) => {
    //       console.log(error, "Error");
    //     });
    // },
    searchMovie(nome) {
      // this.search = nome.toLowerCase();
      axios
        .get(this.api + "/movie", {
          params: {
            api_key: this.apiKey,
            query: nome,
            // CORREZIONE
            language: "it-IT",
          },
        })
        .then((res) => {
          this.movieList = res.data.results;
          console.log(this.movieList);
        })
        .catch((error) => {
          console.log(error, "Error");
        });
      axios
        .get(this.api + "/tv", {
          params: {
            api_key: this.apiKey,
            query: nome,
            language: "it-IT",
          },
        })
        .then((res) => {
          this.tvList = res.data.results;
          console.log(this.tvList);
        })
        .catch((error) => {
          console.log(error, "Error");
        });
      nome = "";
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
}
</style>
