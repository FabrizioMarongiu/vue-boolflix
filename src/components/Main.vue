<template>
  <main>
    <ul>
      <div class="rowFilm" v-show="arrayMovies.length">
        <h2>Film</h2>
        <div class="d-flex">
          <li v-for="element in arrayMovies" :key="element.id">
            <Movie :movies="element" />
          </li>
        </div>
      </div>
      <div class="rowSeries" v-show="arraySeries.length">
        <h2>Serie Tv</h2>
        <div class="d-flex">
          <li v-for="element in arraySeries" :key="element.id">
            <Movie :movies="element" />
          </li>
        </div>
      </div>

      <div
        class="rowHome"
        :class="{ active: !arrayMovies.length, active: !arraySeries.length }"
      >
        <h2>Film in teatro</h2>
        <div class="d-flex">
          <li v-for="element in arrayHome" :key="element.id">
            <Movie :movies="element" />
          </li>
        </div>
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
    arrayHome: Array,
  },

  methods: {},
};
</script>

<style scoped lang="scss">
main {
  flex-grow: 1;
  background-color: #000000;
  overflow-y: auto;
  padding: 35px;
}
.rowFilm,
.rowSeries,
.rowHome {
  overflow-x: auto;
}
h2 {
  margin-left: 35px;
  color: #fff;
}
.d-flex {
  display: flex;
}
li {
  list-style: none;
  padding: 0;
}
.rowHome {
  display: none;
}
.active {
  display: inline;
}
</style>