<template>
  <div in="App">
    <Header @sendRequest="searchMovie" />

    <Main :array="filterArray" />
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
      api:
"https://api.themoviedb.org/3/search/movie?api_key=e12447a41ebd0cc2c67454fb0200dd04"
      apiTv:
        "https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it-IT&query=scrubs",
      movieList: [],
      tvList: [],
      search: "",
    };
  },
  computed: {
    filterArray() {
      if (this.search === "") {
        return this.movieList;
      }

      return this.movieList.filter((element) => {
        return element.title.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },
  created() {
    this.getMovie();
  },
  methods: {
    getMovie() {
      axios
        .get(this.api)
        .then((res) => {
          this.movieList = res.data.results;
          console.log(this.movieList);
        })
        .catch((error) => {
          console.log(error, "Error");
        });
      axios
        .get(this.apiTv)
        .then((res) => {
          this.movieList.push(res.data.results);
          console.log(this.movieList);
        })
        .catch((error) => {
          console.log(error, "Error");
        });
    },
    searchMovie(nome) {
      this.search = nome;
      console.log(this.search);
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
