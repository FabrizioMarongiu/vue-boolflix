<template>
  <header>
    <img
      src="https://fontmeme.com/permalink/210510/ce5edf5ce8ab32d345cb4e38d3af4014.png"
      alt="https://fontmeme.com/permalink/210510/ce5edf5ce8ab32d345cb4e38d3af4014.png"
      class="transparent"
    />
    <form>
      <button @click.prevent="$emit('sendRequest', nome)">Cerca</button>
      <input
        type="text"
        placeholder="Ricerca film o serie"
        v-model.trim="nome"
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
    };
  },
};
</script>

<style scoped lang="scss">
header {
  flex-grow: 1;
  height: 60px;
  background-color: dodgerblue;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}
img {
  width: 150px;
  height: auto;
}
button {
  margin-right: 20px;
}
</style>