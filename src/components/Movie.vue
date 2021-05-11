<template>
  <div class="cardMovie" v-if="movies">
    <h3>
      {{
        movies.title === undefined
          ? `Titolo:  ${movies.name}`
          : `Titolo: ${movies.title}`
      }}
    </h3>
    <h3>
      {{
        movies.original_title === undefined
          ? `Titolo:  ${movies.original_name}`
          : `Titolo: ${movies.original_title}`
      }}
    </h3>
    <!-- DIV CONTENENTE LA BANDIERA -->

    <div class="language">
      <h3>Lingua:</h3>
      <!-- <img
        :src="
            language.includes(movies.original_language)
            ? '@/assets/flags-boolfix/{{movies.original_language}}.png'
            : '{{movies.original_language}}'
        "
        alt=""
        /> -->
      <img
        v-if="movies.original_language === 'it'"
        src="@/assets/flags-boolflix/it.png"
        alt=""
      />
      <img
        v-if="movies.original_language === 'en'"
        src="@/assets/flags-boolflix/en.png"
        :alt="movies.original_language"
      />
      <span v-else>{{ movies.original_language }}</span>
    </div>
    <!-- DIV CONTENENTE I VOTI -->
    <div class="vote">
      <h3>Voto:</h3>
      <i
        class="fas fa-star yellow"
        v-for="(element, index) in parseInt(movies.vote_average / 2)"
        :key="index"
      ></i>
      <i
        class="fas fa-star"
        v-for="(element, index) in 5 - parseInt(movies.vote_average / 2)"
        :key="'A' + index"
      ></i>
    </div>
    <div class="image">
      <img
        :src="`https://image.tmdb.org/t/p/w342/${movies.poster_path}`"
        :alt="movies.title === undefined ? `${movies.name}` : `${movies.title}`"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: ["movies"],
  language: ["it", "en"],
};
</script>

<style scoped lang="scss">
.cardMovie {
  margin: 20px;
}
.language img {
  width: 35px;
  margin: 0 5px;
}
.language,
.vote {
  display: flex;
}
.yellow {
  color: yellow;
}
</style>