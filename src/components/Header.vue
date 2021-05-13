<template>
  <!-- HEADER DELL'APP CHE PERMETTE DI FARE UNA RICERCA PER IL PROPRIO FILM O SERIE TV -->
  <header>
    <img
      src="https://fontmeme.com/permalink/210512/9f74a247396f4711d244938049ad7594.png"
      alt="https://fontmeme.com/permalink/210510/ce5edf5ce8ab32d345cb4e38d3af4014.png"
      class="transparent"
    />
    <form>
      <i class="fas fa-search" @click="search()" v-show="!searchVisible"></i>
      <i class="fas fa-times" @click="search()" v-show="searchVisible"></i>
      <button
        @click.prevent="
          $emit('sendRequest', nome);
          clear();
        "
        :class="{ active: searchVisible }"
      >
        Cerca
      </button>
      <input
        type="text"
        placeholder="Ricerca film o serie"
        v-model.trim="nome"
        :class="{ active: searchVisible }"
      />
    </form>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      nome: "",
      searchVisible: false,
    };
  },
  methods: {
    // FUNZINE PER CANCELLARE LA PAROLA CERCATA DALL'INPUT APPENA FINITA LA RICERCA
    clear() {
      this.nome = "";
    },
    search() {
      this.searchVisible = !this.searchVisible;
      console.log(this.searchVisible);
    },
  },
};
</script>

<style scoped lang="scss">
header {
  min-height: 80px;
  background: linear-gradient(315deg, #000000, #535252, #000000);
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  box-shadow: 1px 0px 10px rgb(69, 41, 41);
  img {
    width: 150px;
    height: auto;
  }
  form {
    position: relative;
  }
  button {
    background-color: #5118d5;
    border: none;
    width: 70px;
    height: 30px;
    border-radius: 20px;
    position: absolute;
    top: 0;
    right: -1px;
    color: grey;
    box-shadow: 1px 0px 10px rgb(69, 41, 41);
    cursor: pointer;
    display: none;
  }
  input {
    border-radius: 20px;
    border: none;
    width: 400px;
    height: 30px;
    padding-left: 10px;
    display: none;
    background-color: #504f4f;
    box-shadow: 1px 0px 10px rgb(69, 41, 41);
  }
  &:focus {
    outline: none;
  }
  i {
    color: #fff;
    font-size: 20px;
    cursor: pointer;
    margin: 0 10px;
  }
  .active {
    display: inline-block;
  }
}
</style>