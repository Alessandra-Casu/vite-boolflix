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
  ></ResultsList>
</template>

<style></style>
