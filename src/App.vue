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
      api: "https://api.themoviedb.org/3/search/movie",
      apiTv: "https://api.themoviedb.org/3/search/tv",
      movieList: [],
      tvList: [],
      search: "",
      apiKey: "e12447a41ebd0cc2c67454fb0200dd04",
      newArray: [],
    };
  },
  computed: {
    filterArray() {
      if (this.search === "") {
        return this.movieList;
      }
      if (this.movieList.length != 0 && this.tvList.length != 0) {
        this.newArray = [];
        this.movieList.forEach((element) => {
          this.newArray.push(element);
        });
        this.tvList.forEach((element) => {
          this.newArray.push(element);
        });
        console.log(this.newArray);
        return this.newArray;
      }
      if (this.movieList.length != 0) {
        return this.movieList.filter((element) => {
          return element.title
            .toLowerCase()
            .includes(this.search.toLowerCase());
        });
      }
      if (this.tvList.length != 0) {
        return this.tvList.filter((element) => {
          return element.name.toLowerCase().includes(this.search.toLowerCase());
        });
      }
    },
  },
  created() {
    // this.getMovie();
  },
  methods: {
    getMovie() {
      axios
        .get(this.api, {
          params: {
            api_key: this.apiKey,
            query: this.search,
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
        .get(this.apiTv, {
          params: {
            api_key: this.apiKey,
            query: this.search,
          },
        })
        .then((res) => {
          this.tvList = res.data.results;
          console.log(this.tvList);
        })
        .catch((error) => {
          console.log(error, "Error");
        });
    },
    searchMovie(nome) {
      this.search = nome.toLowerCase();
      console.log(this.search);

      this.getMovie();
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
