<template>
  <!-- SEZIONE DOVE SI VISUALIZZANO I FILM E LE SERIE TV -->
  <!-- PRIMA PARTE DEDICATA ALL'IMMAGINE DI COPERTINA DEL FILM -->
  <div class="cardMovie" v-if="movies">
    <img
      v-if="movies.poster_path"
      class="image"
      :src="`https://image.tmdb.org/t/p/w342/${movies.poster_path}`"
      :alt="movies.title === undefined ? `${movies.name}` : `${movies.title}`"
    />
    <img
      class="image"
      v-else
      src="https://www.altavod.com/assets/images/poster-placeholder.png"
      :alt="movies.title === undefined ? `${movies.name}` : `${movies.title}`"
    />
    <!-- LA SECONDA PARTE è DEDIVATA ALLA DESCRIZIONE/TITOLO/VOTO E SI ATTIVA IN HOVER SULL'ELEMENTO -->
    <div class="back">
      <h3>
        {{
          movies.title ? `Titolo: ${movies.title}` : `Titolo:  ${movies.name}`
        }}
      </h3>
      <h3
        v-show="
          movies.title != movies.original_title ||
          movies.name != movies.original_name
        "
      >
        <!-- <h3> -->
        {{
          movies.original_title
            ? `Titolo originale: ${movies.original_title}`
            : `Titolo originale:  ${movies.original_name}`
        }}
      </h3>
      <div class="overview">
        <h3>Overview:</h3>
        <span> {{ movies.overview }}</span>
      </div>
      <!-- DIV CONTENENTE LA BANDIERA -->

      <div class="language">
        <h3>Lingua:</h3>

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
        <span
          v-show="
            movies.original_language != 'it' && movies.original_language != 'en'
          "
          >{{ movies.original_language }}</span
        >
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
    </div>
  </div>
</template>

<script>
export default {
  name: "Movie",
  props: ["movies"],
  data() {
    return {
      language: ["it", "en"],
    };
  },
};
</script>

<style scoped lang="scss">
.cardMovie {
  margin: 20px 10px;
  color: #fff;
  position: relative;
  min-height: 513px;
  max-height: 513px;
  min-width: 342px;
  cursor: pointer;
  overflow: hidden;
  transition: 2s;
  .language img {
    width: 35px;
    margin: 0 5px;
  }
  .language,
  .vote {
    display: flex;
  }
  .overview h3 {
    display: inline;
  }
  .overview span {
    font-size: 12px;
  }
  .yellow {
    color: yellow;
  }
  .back {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.43);
    opacity: 0;
    transition: 0.5s;
    padding: 20px;
    text-align: left;
  }
  &:hover {
    box-shadow: 1px 0px 10px rgba(168, 163, 163, 0.786);
    transform: scale(1.1);
    .back {
      opacity: 2;
    }
  }
  .image {
    width: 100%;
    height: 100%;
    filter: brightness(80%);
  }
}

/**
TO FIXED
 */
// .cardMovie:hover ~ .cardMovie {
//   transform: translateX(25%);
// }
</style>