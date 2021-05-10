<template>
  <div class="cardMovie">
    <h3>Titolo: {{ movies.title }}</h3>
    <h3>Titolo Originale: {{ movies.original_title }}</h3>
    <h3>Lingua: {{ movies.original_language }}</h3>
    <h3>Voto: {{ movies.vote_average }}</h3>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: ["movies"],
};
</script>

<style scoped lang="scss">
.cardMovie {
  margin: 20px;
}
</style>