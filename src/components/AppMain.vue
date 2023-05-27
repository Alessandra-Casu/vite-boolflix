<script>
import ResultsList from "./ResultsList.vue";
import { store } from "../store";

export default {
  data() {
    return {
      store,
    };
  },
  components: {
    ResultsList,
  },
};
</script>

<template>
  <ResultsList
    listTitle="Risultati dei film"
    :arrCards="store.arrMovies"
    :cardType="movie"
  ></ResultsList>
  <ResultsList
    listTitle="Risultati delle serie"
    :arrCards="store.arrSeries"
    :cardType="serie"
  ></ResultsList>
</template>

<style></style>
