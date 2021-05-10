<template>
  <main>
    <ul>
      <li v-for="(element, index) in movieList" :key="index">
        <Movie :movies="element" />
      </li>
    </ul>
  </main>
</template>

<script>
import axios from "axios";
import Movie from "@/components/Movie.vue";

export default {
  name: "Main",
  components: {
    Movie,
  },
  data() {
    return {
      api:
        "https://api.themoviedb.org/3/search/movie?api_key=e12447a41ebd0cc2c67454fb0200dd04&query=avengers&language=it-IT",
      movieList: [],
    };
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
    },
  },
};
</script>

<style scoped lang="scss">
li {
  margin: 20px;
}
</style>