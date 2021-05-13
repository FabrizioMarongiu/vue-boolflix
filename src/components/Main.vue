<template>
  <!-- SEZIONE DEDICATA AL MAIN DOVE SI VUSUALIZZANO GLI ELENCHI DELLE RICERCHE EFFETTUATE -->
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
      <!-- QUESTA SEZIONE SI POPOLA ALL'AVVIO DELL'APP E MOSTRA I FILM PRESENTI IN TEATRO  -->
      <div class="rowHome" v-show="!arrayMovies.length && !arraySeries.length">
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
  .rowFilm,
  .rowSeries,
  .rowHome {
    overflow-x: auto;
    height: 650px;
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
}
</style>