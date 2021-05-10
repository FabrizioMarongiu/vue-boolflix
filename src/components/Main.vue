<template>
  <main>
    <ul>
      <li v-for="(element, index) in array" :key="index">
        <Movie :movies="element" />
      </li>
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
  props: ["array"],

  methods: {},
};
</script>

<style scoped lang="scss">
li {
  margin: 20px;
}
</style>