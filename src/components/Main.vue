<template>
  <main>
    <ul>
      <div v-show="arrayMovies.length">
        <span>Film</span>
        <li v-for="element in arrayMovies" :key="element.id">
          <Movie :movies="element" />
        </li>
      </div>
      <div v-show="arraySeries.length">
        <span>Serie Tv</span>
        <li v-for="element in arraySeries" :key="element.id">
          <Movie :movies="element" />
        </li>
      </div>
    </ul>
  </main>
</template>

<script>
import Movie from "@/components/Movie.vue";

export default {
  name: "Main",
  components: {
    Movie,
  },
  props: {
    arrayMovies: Array,
    arraySeries: Array,
  },

  methods: {},
};
</script>

<style scoped lang="scss">
li {
  margin: 20px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>